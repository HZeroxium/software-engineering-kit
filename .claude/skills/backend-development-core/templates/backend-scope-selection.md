# Backend Scope Selection

## User Request

`<paste or summarize the request>`

## Scope Selection Result

| Rank | Scope               | Fit        | Reason     |
| ---: | ------------------- | ---------- | ---------- |
|    1 | `<primary scope>`   | High       | `<reason>` |
|    2 | `<secondary scope>` | Medium     | `<reason>` |
|    3 | `<secondary scope>` | Low/Medium | `<reason>` |

## 9-Scope Routing Map

| Scope                                               | Use When                                                                                                                       | Do Not Use When                                                                |
| --------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ |
| `backend-domain-and-api-design`                     | Domain concepts, API contracts, business workflows, versioning, error models, idempotency                                      | The task is only about runtime deployment or infrastructure                    |
| `backend-application-architecture`                  | Use-case orchestration, transaction boundaries, module boundaries, dependency architecture, workflow design                    | The user only needs API naming or schema syntax                                |
| `backend-data-and-persistence`                      | Schema, indexes, queries, migrations, transactions, consistency, cache correctness, data lifecycle                             | The task has no state or persistence concern                                   |
| `backend-security-and-trust`                        | AuthN/AuthZ, object-level authorization, tenant isolation, secrets, sensitive data, threat modeling                            | The task has no trust boundary or sensitive operation                          |
| `backend-integration-and-distributed-communication` | RPC, APIs, queues, events, retries, timeouts, circuit breakers, idempotent consumers, outbox/inbox                             | The task is local-only and has no network/message boundary                     |
| `backend-reliability-and-resilience`                | SLOs, availability, failure handling, failover, degradation, incident readiness                                                | The task is only about code style or naming                                    |
| `backend-performance-and-scalability`               | Latency, throughput, p95/p99, capacity, database performance, concurrency, load testing, cost-performance                      | No load, latency, or resource constraint exists                                |
| `backend-observability-and-operations`              | Metrics, logs, traces, alerts, dashboards, runbooks, CI/CD, release, health checks, runtime config                             | The task has no production or operational concern                              |
| `backend-ai-governance-and-quality`                 | AI backend integration, RAG, model calls, agents, prompts, evaluation, AI observability, privacy, compliance, testing strategy | The task is deterministic backend logic with no AI/governance/quality emphasis |

## Scope Fit Explanation

### Primary Scope

`<why this is the primary scope>`

### Secondary Scopes

- `<scope>`: `<why it is secondary>`
- `<scope>`: `<why it is secondary>`

## Specialized Skill Routing

| Recommended Skill | Reason     | Handoff Needed? |
| ----------------- | ---------- | --------------: |
| `<skill>`         | `<reason>` |      `<yes/no>` |

## Next Decision

`<ask user for context / proceed to handoff / recommend onboarding / recommend design analysis>`
