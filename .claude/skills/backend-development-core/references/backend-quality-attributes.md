---
purpose: 17 quality attributes for evaluating backend designs beyond correctness; includes trade-off table and validation evidence examples
load-when: Evaluating a backend design, identifying trade-offs, or defining the quality bar for a task
tier: domain
see-also: []
---

# Backend Quality Attributes

## Purpose

Use quality attributes to evaluate backend designs beyond “does it work”. These attributes help classify risks, trade-offs, and implementation priorities.

## Core Quality Attributes

| Attribute       | Meaning                                                       | Common Signals                               |
| --------------- | ------------------------------------------------------------- | -------------------------------------------- |
| Correctness     | System enforces expected behavior and business rules          | Tests, invariants, validation, consistency   |
| Security        | System protects identities, resources, secrets, and data      | AuthN/AuthZ, tenant isolation, audit logs    |
| Reliability     | System continues to behave acceptably under expected failures | SLOs, retries, fallbacks, incident readiness |
| Availability    | System can serve users when needed                            | redundancy, failover, health checks          |
| Resilience      | System absorbs, recovers, or degrades under failure           | circuit breakers, bulkheads, degradation     |
| Performance     | System meets latency and throughput targets                   | p95/p99, resource usage, query plans         |
| Scalability     | System handles growth in traffic, data, tenants, or features  | partitioning, horizontal scaling, capacity   |
| Maintainability | System can be safely understood and changed                   | modularity, tests, docs, dependency clarity  |
| Evolvability    | System supports future changes without excessive rewrites     | stable contracts, versioning, boundaries     |
| Operability     | System is easy to deploy, observe, debug, and recover         | CI/CD, runbooks, alerts, dashboards          |
| Observability   | System behavior can be inferred from emitted signals          | metrics, logs, traces, correlation           |
| Testability     | System can be validated deterministically                     | isolated tests, integration tests, fixtures  |
| Data integrity  | System preserves valid and durable data                       | constraints, transactions, migrations        |
| Privacy         | System minimizes and protects sensitive data                  | PII classification, masking, retention       |
| Cost efficiency | System meets goals with acceptable cost                       | capacity, telemetry cost, provider cost      |
| Compliance      | System satisfies applicable obligations                       | audit evidence, policies, retention          |
| AI quality      | AI output is evaluated, monitored, and governed               | evals, human review, AI observability        |

## Attribute Trade-Offs

| Trade-Off                     | Example                                                      |
| ----------------------------- | ------------------------------------------------------------ |
| Consistency vs availability   | Strong consistency may reduce availability during partitions |
| Performance vs correctness    | Cache can improve latency but introduce stale data           |
| Security vs usability         | Stronger verification can add friction                       |
| Observability vs cost/privacy | More telemetry can increase cost and sensitive-data risk     |
| Flexibility vs simplicity     | Too many abstractions can harm maintainability               |
| Reliability vs cost           | Redundancy and failover increase infrastructure cost         |
| AI quality vs latency/cost    | Better models or reranking may increase cost and latency     |

## How to Use

For each backend task:

1. Identify the top 3 quality attributes that matter most.
2. Identify attributes that may conflict.
3. State the trade-off explicitly.
4. Recommend the simplest design that satisfies the required quality bar.
5. Define validation evidence.

## Validation Evidence Examples

| Attribute     | Evidence                                            |
| ------------- | --------------------------------------------------- |
| Correctness   | Unit/integration/contract tests, invariant checks   |
| Security      | Threat model, access-control tests, secret scanning |
| Reliability   | SLOs, failure-mode tests, runbooks                  |
| Performance   | Benchmarks, load tests, traces, query plans         |
| Observability | Dashboards, alerts, log/trace correlation           |
| Operability   | CI/CD pipeline, rollback plan, health checks        |
| Privacy       | Data classification, masking, retention tests       |
| AI quality    | Eval dataset, scoring, regression thresholds        |
