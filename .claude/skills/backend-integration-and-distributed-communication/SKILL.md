---
name: backend-integration-and-distributed-communication
description: Framework-agnostic backend Skill for service integration, RPC/internal APIs, async messaging, event contracts, webhooks, external APIs, retries, timeouts, deadlines, idempotency, outbox/inbox, sagas, compensation, and distributed failure modes.
---

# Backend Integration and Distributed Communication

Use this Skill when a backend task involves service-to-service communication, RPC/internal APIs, message queues, pub/sub, event streams, webhooks, external APIs, retries, timeouts, idempotency, outbox/inbox, or distributed workflows.

## Purpose

Analyze backend service integration and distributed communication.

This Skill covers:

- Synchronous APIs and RPC.
- Asynchronous messaging.
- Event contracts.
- API Gateway and BFF boundaries.
- Retries, timeouts, and deadlines.
- Circuit breakers, bulkheads, and backpressure.
- Idempotent consumers.
- Outbox/inbox patterns.
- Sagas and compensation.
- Distributed failure modes.

## Non-Goals

Do not:

- Assume Kafka, RabbitMQ, gRPC, REST, Kubernetes, service mesh, or cloud-specific infrastructure.
- Invent queue semantics, retry library behavior, delivery guarantees, or internal infrastructure behavior.
- Assume exactly-once delivery.
- Recommend retries without idempotency analysis.
- Ignore observability for distributed calls.

## Workflow

1. Identify caller, callee, contract, and communication style.
2. Classify sync vs async interaction.
3. Analyze contract/schema compatibility.
4. Define timeout, deadline, retry, and cancellation behavior.
5. Analyze idempotency and duplicate handling.
6. Identify distributed failure modes and recovery behavior.
7. Evaluate circuit breaker, bulkhead, backpressure, outbox/inbox, saga, or compensation needs.
8. Define test and observability plan.
9. Separate confirmed facts, assumptions, hypotheses, and unknowns.

## Expected Output

Return:

- Communication style analysis.
- Contract/schema risks.
- Timeout/retry/deadline policy.
- Idempotency and duplicate handling.
- Failure modes.
- Compensation/outbox/inbox strategy if relevant.
- Test and observability plan.
- Open questions and required repo evidence.

## Safety Boundaries

Ask for clarification or repo evidence when:

- Internal infrastructure abstractions define retry, timeout, messaging, or RPC behavior.
- Delivery semantics are unclear.
- The operation has external side effects.
- The workflow touches payments, orders, notifications, data mutation, or production integrations.
- Retry behavior could amplify load or cause duplicate effects.
