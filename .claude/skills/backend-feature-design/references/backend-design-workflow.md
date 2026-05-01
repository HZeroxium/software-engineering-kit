# Backend Design Workflow

## Principle

Backend design should start from capability and behavior, not from framework classes or database tables.

## Workflow

1. **Understand feature intent**
   - Identify actor, goal, current behavior, desired behavior, and constraints.

2. **Model domain**
   - Identify concepts, invariants, valid state transitions, and business rules.

3. **Design interface**
   - Choose API/RPC/event/job/internal interface shape.
   - Define request, response, errors, idempotency, and compatibility.

4. **Design application workflow**
   - Define orchestration steps, transaction boundaries, side effects, async work, and compensation.

5. **Design data impact**
   - Identify reads/writes, ownership, schema, indexes, migrations, caching, and data lifecycle.

6. **Design security/trust**
   - Identify authentication, authorization, object-level checks, tenant isolation, secrets, audit, and sensitive data.

7. **Design integration behavior**
   - Define sync/async boundaries, contracts, timeouts, retries, idempotency, and backpressure.

8. **Design reliability/performance/observability**
   - Define failure modes, fallback, latency/throughput assumptions, metrics, logs, traces, alerts, and runbooks.

9. **Design validation**
   - Define unit, integration, contract, security, performance, resilience, observability, and manual review evidence.

10. **Prepare implementation handoff**

- Summarize design, risks, affected modules, validation commands, and open questions.

## Design Quality Bar

A backend design is ready for implementation when:

- Business behavior is explicit.
- Contract and compatibility are clear.
- Data and transaction impact are clear.
- Security and trust boundaries are clear.
- Failure handling is defined.
- Validation strategy is concrete.
- Open questions are visible.
