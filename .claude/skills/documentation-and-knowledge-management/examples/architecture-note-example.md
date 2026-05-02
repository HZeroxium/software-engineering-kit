# Architecture Note Example: Order Event Publishing — Sync HTTP to Async Queue

This example demonstrates how to write an architecture note grounded in current
behavior, with current and proposed architecture clearly separated, key decisions
justified, and unknowns explicitly marked.

---

# Architecture Note

## Title

Order Event Publishing: Migrate from Synchronous HTTP Callback to Async Message Queue

## Context

Currently, the order service notifies downstream consumers (notification service,
inventory service, analytics pipeline) via synchronous HTTP calls immediately after
an order is persisted. This creates tight coupling and cascading failures: if any
downstream service is slow or unavailable, the order creation latency degrades and
the order creation transaction may time out.

Source evidence:
- Order service creates HTTP clients for each downstream in `OrderCreationHandler`
- Integration tests reveal 3 downstream calls are made synchronously before HTTP 200 is returned
- Latency p99 on order creation is ~1200ms; downstream call timeout is 800ms
- Post-incident review (linked ticket) traced 3 incidents to downstream unavailability causing order creation failures

Constraints:
- Order creation must remain under 200ms p99.
- Downstream consumers must receive events within 5 seconds under normal load.
- No customer data loss is acceptable.

## Current Architecture

Ground in current code, configs, and verified behavior.

- **Components**:
  - `OrderCreationHandler` — owns the HTTP request lifecycle and downstream notification
  - `NotificationHttpClient`, `InventoryHttpClient`, `AnalyticsHttpClient` — synchronous HTTP clients, called inline
  - No retry or circuit-breaker logic for downstream calls
- **Data flow**: `POST /orders` → persist order → call 3 downstream services synchronously → return 200
- **Integration points**: 3 downstream HTTP endpoints, all called inline before response
- **Known limitations**:
  - Downstream failure rolls back or delays order creation
  - No deduplication of downstream events
  - Analytics call is fire-and-forget but still blocks response

## Proposed Architecture

- **Components**:
  - `OrderCreationHandler` — persist order, publish event, return 200 (no downstream calls inline)
  - `OrderEventPublisher` — publishes `OrderCreatedEvent` to the message queue after commit
  - Message queue topic: `order.created` (topic name TBD — see Open Questions)
  - `NotificationConsumer`, `InventoryConsumer`, `AnalyticsConsumer` — async subscribers, each independently consuming `order.created`
- **Data flow**: `POST /orders` → persist order → publish event (post-commit) → return 200; consumers process asynchronously
- **API changes**: No public API changes. Response contract unchanged.
- **Persistence changes**: No schema change required. Event payload is derived from existing `Order` entity.
- **Operational changes**: Requires message queue infrastructure (broker, topic config, consumer group config).

## Key Decisions

| Decision | Rationale | Trade-off |
|----------|-----------|-----------|
| Publish event post-commit, not pre-commit | Avoids publishing an event for a transaction that may roll back | If publish fails after commit, event is lost — requires outbox pattern or at-least-once delivery guarantee |
| Keep downstream consumers independent | Each consumer can fail, retry, and scale independently | Consumers may process events out of order under high load |
| No schema change | Reuses existing `Order` entity fields | Event payload may carry more fields than consumers need |

## Alternatives Considered

### Alternative 1: Outbox Pattern

- **Summary**: Write event to an `order_outbox` table in the same transaction as order creation; a poller or CDC mechanism forwards events to the queue.
- **Pros**: Guarantees event is published if and only if the order is committed. No lost events.
- **Cons**: Requires schema change, outbox table management, and polling/CDC infrastructure.
- **Why not selected**: Higher complexity. Evaluate if lost-event risk materializes after initial rollout.

### Alternative 2: Keep Synchronous Calls with Circuit Breaker

- **Summary**: Add Resilience4j circuit breakers and timeouts to existing HTTP clients.
- **Pros**: No infrastructure change. Preserves synchronous model.
- **Cons**: Does not eliminate coupling. Downstream slowness still adds latency. Partial failures remain hard to reason about.
- **Why not selected**: Does not address the root cause — downstream calls should not be on the critical path.

## Risks and Mitigations

| Risk | Impact | Mitigation |
|------|--------|------------|
| Event published but not consumed (consumer down) | Downstream state diverges temporarily | Queue durability + consumer retry with DLQ |
| Event lost between commit and publish (JVM crash) | Order created but no downstream notification | Accept as known limitation in v1; evaluate outbox pattern post-launch |
| Duplicate event delivery | Downstream processes order twice | Consumers must be idempotent; include order ID in event |
| Consumer lag under high load | Analytics and inventory lag behind orders | Set alerting on consumer lag; consumers scale independently |

## Security Considerations

- **Authentication**: Queue access must require service identity (not open to all services).
- **Authorization**: Only `order-service` may publish to `order.created`; consumers have read-only access.
- **Sensitive data**: Event payload must not include full customer PII (name, address, payment details) — include only order ID, restaurant ID, and timestamp.
- **Auditability**: Publish and consume events should be logged with trace IDs for incident analysis.

## Observability Considerations

- **Logs**: Log event publish success/failure with order ID and trace ID.
- **Metrics**: `order.event.published` (count), `order.event.publish.failure` (count), consumer lag per topic.
- **Traces**: Propagate trace context from order creation into the event; consumers continue the trace.
- **Alerts**: Alert on consumer lag > 30s, publish failure rate > 1%, DLQ depth > 0.

## Validation Plan

- Unit tests: `OrderEventPublisher` publishes correct payload; no downstream calls in `OrderCreationHandler`.
- Integration tests: Order creation triggers exactly one event on the queue; consumers receive and process it.
- Load test: Order creation p99 meets <200ms target with downstream consumers detached.
- Manual review: Security team reviews event payload for PII exposure.

## Rollback Plan

- Feature flag `order.async-events.enabled` gates the new publish path.
- Disabling the flag reverts to synchronous HTTP calls (existing path preserved for rollback window).
- Remove flag and synchronous path after 2 weeks of stable operation.

## Open Questions

- **[BLOCKING]** Which message broker is available in the current infrastructure? (Kafka, RabbitMQ, SQS?) This affects topic naming, consumer group config, and durability guarantees.
- **[BLOCKING]** What is the acceptable event delivery SLA for notification service? (Affects whether outbox pattern is required for v1.)
- **[DECISION NEEDED]** Should the event payload include full order line items, or only order ID and metadata?
- **[ASSUMPTION]** Consumer idempotency is the responsibility of each downstream team. Confirm with notification and inventory teams.
