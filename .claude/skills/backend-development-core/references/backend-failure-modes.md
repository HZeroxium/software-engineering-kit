# Backend Failure Modes

## Purpose

Use this reference to identify likely backend failure modes during task triage.

## Domain and API Failure Modes

- API shape mirrors database tables rather than business behavior.
- Missing business invariants.
- Inconsistent error model.
- Breaking changes without versioning.
- Missing idempotency for retryable operations.
- Unbounded result sets.
- Ambiguous ownership of domain concepts.

## Application Architecture Failure Modes

- Business logic in controllers/handlers.
- Large service classes with mixed responsibilities.
- Transaction boundary too broad or too narrow.
- Side effects inside fragile transactions.
- Background jobs without idempotency.
- State transitions modeled implicitly.
- Dependency cycles.
- Internal framework behavior assumed but not verified.

## Data and Persistence Failure Modes

- Missing data ownership boundary.
- Unsafe schema migration.
- Missing indexes.
- Lock contention.
- Cache invalidation bug.
- Inconsistent reads after writes.
- Cross-tenant data leakage.
- Analytics query overloading production OLTP database.
- Data retention/deletion missing.

## Security and Trust Failure Modes

- Authentication without authorization.
- Missing object-level authorization.
- Tenant ID spoofing.
- Secrets in logs/config/code.
- Sensitive data in API responses.
- Missing audit trail.
- Excessive service-to-service trust.
- Unsafe deserialization or injection.
- Abuse controls missing.

## Integration and Distributed Communication Failure Modes

- Missing timeouts.
- Retry storms.
- Retrying non-idempotent operations.
- Assuming exactly-once delivery.
- Duplicate message side effects.
- Event schema incompatibility.
- Outbox missing for reliable publish.
- Consumer lag/backpressure ignored.
- Gateway becomes distributed monolith.

## Reliability and Resilience Failure Modes

- No SLO/SLI.
- User impact not monitored.
- Dependency failure causes cascading failure.
- No graceful degradation.
- Shared resource pools cause saturation.
- Backup restore untested.
- Incident runbook missing.
- Failover path not exercised.

## Performance and Scalability Failure Modes

- Optimizing without measurement.
- Average latency hides p99 issues.
- N+1 queries.
- Chatty network calls.
- Unbounded concurrency.
- Thread/connection pool exhaustion.
- Inefficient serialization.
- Cache stampede.
- Hot partitions.
- Cost grows faster than traffic.

## Observability and Operations Failure Modes

- Logs lack correlation IDs.
- Metrics have uncontrolled cardinality.
- Alerts are noisy or unactionable.
- Dashboards do not show user impact.
- Health checks do not validate dependencies.
- Rollback path missing.
- CI/CD skips critical tests.
- Runtime config changes are unaudited.

## Testing and Quality Failure Modes

- Happy-path-only tests.
- Over-mocking hides integration bugs.
- No contract tests.
- No migration tests.
- Flaky E2E tests.
- No failure-mode tests.
- No performance regression checks.
- No observability assertions.

## Governance and Privacy Failure Modes

- Sensitive data not classified.
- Retention/deletion unclear.
- Audit evidence missing.
- Vendor risk ignored.
- No ADR for major decisions.
- Compliance considered after release.
- Cost owner unclear.

## Applied AI Backend Failure Modes

- AI used where deterministic logic is safer.
- Prompt injection unhandled.
- Sensitive data sent to models unnecessarily.
- Tool calls can cause side effects without approval.
- No eval dataset.
- No hallucination/quality monitoring.
- No fallback when model provider fails.
- Token/cost usage unbounded.
- RAG retrieval quality unmeasured.
