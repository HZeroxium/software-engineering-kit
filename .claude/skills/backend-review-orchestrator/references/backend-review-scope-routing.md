---
purpose: Routing table mapping change signals to backend review scopes; multi-scope examples for common change types
load-when: Classifying which backend scopes are affected by a given diff, PR, or design change
tier: foundational
see-also:
  - backend-production-risk-model.md
  - backend-review-workflow.md
---

# Backend Review Scope Routing

## Scope Routing

| Change Signal                                   | Route To                                |
| ----------------------------------------------- | --------------------------------------- |
| API contract, DTO, error model, versioning      | Domain/API                              |
| Business rules, validation, state transitions   | Domain/API and application architecture |
| Use-case orchestration, transactions, workflows | Application architecture                |
| Schema, migrations, queries, indexes, cache     | Data/persistence                        |
| Auth, authorization, tenant isolation, secrets  | Security/trust                          |
| RPC, HTTP clients, messaging, events            | Integration/distributed communication   |
| Timeout, retry, circuit breaker, fallback       | Reliability/resilience and integration  |
| Latency, throughput, DB load, concurrency       | Performance/scalability                 |
| Metrics, logs, traces, alerts, health checks    | Observability/operations                |
| CI/CD, release, config, runtime controls        | Observability/operations                |
| Tests, compliance, privacy, AI model/tool calls | AI/governance/quality                   |

## Multi-Scope Examples

### New API That Writes Data

Review:

- Domain/API contract.
- Application workflow.
- Data consistency.
- Authorization.
- Tests.
- Observability.

### Message Consumer

Review:

- Event contract.
- Duplicate handling.
- Idempotency.
- Retry/backoff.
- Dead-letter behavior.
- Observability.
- Tests.

### AI Backend Feature

Review:

- Prompt/context safety.
- Privacy.
- Tool permission boundaries.
- Output validation.
- Evaluation.
- Cost/latency monitoring.
- Fallback behavior.
