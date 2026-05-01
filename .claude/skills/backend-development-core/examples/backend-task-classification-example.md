# Backend Task Classification Example

## User Request

“I need to add a new API for creating payment orders. It should call an external payment provider, save the order, and allow clients to retry safely if they timeout.”

## Backend Task Classification

### Summary

This is a backend feature design and implementation-planning task involving API contract design, application workflow orchestration, data persistence, external integration, security, idempotency, reliability, and observability.

### Task Type

- Backend feature design.
- Backend feature implementation planning.
- Domain/API design.
- Application architecture analysis.
- Data/persistence analysis.
- Integration/distributed communication analysis.
- Reliability/resilience analysis.
- Observability/operations analysis.
- Security/trust analysis.

### Primary Scope

`backend-integration-and-distributed-communication`

Reason: the riskiest part is the external payment-provider boundary, timeout behavior, retries, idempotency, duplicate handling, and partial failure handling.

### Secondary Scopes

- `backend-domain-and-api-design` — API contract, error model, idempotency key semantics, retryable vs non-retryable errors.
- `backend-application-architecture` — use-case orchestration, transaction boundaries, side effects, compensation.
- `backend-data-and-persistence` — payment order state, uniqueness constraints, transaction safety, audit records.
- `backend-security-and-trust` — authorization, sensitive payment fields, audit logging.
- `backend-reliability-and-resilience` — timeout handling, graceful recovery, provider outage behavior.
- `backend-observability-and-operations` — metrics, logs, traces, alerts, runbook for provider failures.

### Cross-Cutting Concerns

| Concern          | Relevant? | Reason                                                  |
| ---------------- | --------: | ------------------------------------------------------- |
| Error handling   |       Yes | Payment provider and API errors need stable mapping     |
| Idempotency      |       Yes | Client retries must not create duplicate payment orders |
| Configuration    |       Yes | Provider credentials, timeout, retry settings           |
| Multi-tenancy    |  Possibly | Payment order ownership may be tenant-specific          |
| Cost             |  Possibly | Provider calls and retries may create cost              |
| Governance       |       Yes | Payment workflows often require auditability            |
| Observability    |       Yes | Provider latency/failure must be visible                |
| Privacy/security |       Yes | Sensitive payment data may be involved                  |
| Testing          |       Yes | Requires contract, integration, and failure-mode tests  |

### Risk Level

High.

### Risk Rationale

- External payment calls can fail or timeout.
- Retried client requests may create duplicate side effects.
- Payment data may be sensitive.
- Transaction and provider call ordering can create inconsistent state.
- Observability is required for operational support.

### Context Needed

- Existing payment/order domain model.
- Existing API error model.
- Existing idempotency conventions.
- Database schema and uniqueness constraints.
- Provider API contract.
- Existing HTTP/RPC client wrapper conventions.
- Logging/metrics/tracing standards.
- Test harness and validation command.

### Recommended Specialized Skill

`backend-integration-and-distributed-communication`

### Suggested Next Action

Produce a payment-order workflow design before implementation, including API contract, state transitions, idempotency strategy, transaction boundary, provider timeout/retry policy, failure modes, tests, and observability.

### Handoff Prompt

```text
Use the backend-integration-and-distributed-communication Skill.

Task:
Design a backend API for creating payment orders. The API calls an external payment provider, saves the order, and must allow clients to retry safely after timeout.

Primary scope:
backend-integration-and-distributed-communication

Secondary scopes:
backend-domain-and-api-design, backend-application-architecture, backend-data-and-persistence, backend-security-and-trust, backend-reliability-and-resilience, backend-observability-and-operations

Risks:
- Duplicate payment orders under retry.
- Provider timeout or partial failure.
- Sensitive payment data.
- Incorrect transaction boundary.
- Missing auditability and observability.

Do not assume:
- A specific Java framework.
- Spring-specific transaction behavior.
- A specific payment provider API.
- Internal library behavior without repo evidence.

Expected output:
A framework-agnostic design with API contract, state model, idempotency strategy, transaction boundary, retry/timeout policy, failure handling, test plan, observability plan, and implementation notes using Java examples only where useful.
```
