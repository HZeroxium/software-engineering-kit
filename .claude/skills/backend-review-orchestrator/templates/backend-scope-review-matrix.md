# Backend Scope Review Matrix

## Review Target

`<PR/diff/design/files>`

## Matrix

| Scope                                 | Review Questions                                                                                         | Evidence     | Risk     |
| ------------------------------------- | -------------------------------------------------------------------------------------------------------- | ------------ | -------- |
| Domain/API                            | Are business rules, contracts, errors, idempotency, and compatibility correct?                           | `<evidence>` | `<risk>` |
| Application architecture              | Are use-case orchestration, transaction boundaries, dependencies, and workflow responsibilities correct? | `<evidence>` | `<risk>` |
| Data/persistence                      | Are schema, queries, transactions, migrations, cache, and data lifecycle safe?                           | `<evidence>` | `<risk>` |
| Security/trust                        | Are auth, authorization, tenant isolation, secrets, audit, and sensitive data safe?                      | `<evidence>` | `<risk>` |
| Integration/distributed communication | Are timeouts, retries, contracts, idempotency, duplicate handling, and backpressure safe?                | `<evidence>` | `<risk>` |
| Reliability/resilience                | Are failure modes, fallbacks, SLO impact, recovery, and degradation handled?                             | `<evidence>` | `<risk>` |
| Performance/scalability               | Are latency, throughput, p95/p99, database load, concurrency, and capacity risks controlled?             | `<evidence>` | `<risk>` |
| Observability/operations              | Are metrics, logs, traces, alerts, runbooks, config, release, and health checks adequate?                | `<evidence>` | `<risk>` |
| AI/governance/quality                 | Are tests, verification, privacy, compliance, AI eval, AI safety, and governance adequate?               | `<evidence>` | `<risk>` |

## Review Focus

- **Primary focus:** `<scope>`
- **Secondary focus:** `<scope>`
- **Specialized handoff needed:** `<yes/no>`
