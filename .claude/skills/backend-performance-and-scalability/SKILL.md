---
name: backend-performance-and-scalability
description: Framework-agnostic backend Skill for latency, throughput, p95/p99, scalability, bottlenecks, resource usage, database performance, caching, concurrency, load testing, capacity, and cost-performance trade-offs.
---

# Backend Performance and Scalability

Use this Skill when a backend task involves latency, throughput, p95/p99, scaling, bottlenecks, resource usage, database performance, caching, concurrency, load testing, or cost-performance trade-offs.

## Purpose

Analyze backend performance, scalability, efficiency, and cost-performance trade-offs.

This Skill prevents speculative optimization by requiring measurement or clearly labeled hypotheses.

## Non-Goals

Do not:

- Assume performance bottlenecks without evidence.
- Optimize before identifying measurement or hypothesis.
- Assume specific databases, caches, profilers, monitoring tools, or cloud platforms.
- Invent metrics, benchmark commands, load-test tools, or query plans.
- Treat average latency as enough for production performance.
- Review distributed system performance across service boundaries — use `backend-integration-and-distributed-communication` for fan-out, saga latency, and distributed coordination costs.

## Required Inputs

Collect before analysis:

- Performance goal or SLO target (latency budget, throughput, error rate).
- Available evidence: metrics, traces, logs, profiles, query plans, benchmarks, load tests.
- Traffic shape: average load, peak load, growth rate.
- Stack context: database, cache, external dependencies, concurrency model.

If inputs are missing, label conclusions as hypotheses and request measurement.

## Workflow

1. Identify user-visible performance goal.
2. Collect existing evidence if available: metrics, traces, logs, profiles, query plans, benchmarks, load tests.
3. If evidence is missing, label bottlenecks as hypotheses.
4. Analyze latency, throughput, tail latency, resource usage, database, cache, concurrency, and external dependencies.
5. Identify scalability limiters and cost-performance trade-offs.
6. Recommend minimal optimizations ranked by evidence and risk.
7. Define validation metrics and load-test plan.
8. Separate facts, assumptions, hypotheses, and unknowns.

## Expected Outputs

**Output type: mixed**

- Component 1 — `analysis`: bottleneck hypothesis table with evidence, confidence level, and validation steps.
- Component 2 — `plan`: ordered optimization recommendations with risk, validation metrics, and load-test plan.

Return:

- Performance assumptions.
- Existing evidence or missing measurements.
- Bottleneck hypotheses.
- Query/index/cache/concurrency risks.
- Scalability analysis.
- Load-test plan.
- Validation metrics.
- Minimal optimization recommendations.

## Safety Boundaries

Ask for clarification or repo evidence when:

- Performance targets are unknown.
- Data volume, traffic, or latency budgets are missing.
- Proposed optimization changes behavior or consistency.
- Load testing may affect shared or production systems.
- Internal libraries manage concurrency, pooling, caching, or IO behavior.

## Validation

Test this Skill with:

- A PR with a known N+1 query — verify bottleneck hypothesis is identified and load-test plan is recommended.
- A vague "make it faster" request — verify it asks for targets and evidence before recommending optimizations.
- A pure functional bug report — verify this Skill does not activate.

## Supporting Files

| Folder | File | Purpose |
|--------|------|---------|
| `references/` | `reference-index.md` | Semantic graph and load-order guide for all references |
| `references/` | `performance-measurement-discipline.md` | Core principle: measure before optimize |
| `references/` | `latency-throughput-and-tail-latency.md` | Core vocabulary: latency, throughput, p95/p99, saturation |
| `references/` | `database-performance.md` | DB query, index, N+1, and connection pool analysis |
| `references/` | `caching-performance.md` | Cache hit rate, invalidation, and correctness risks |
| `references/` | `concurrency-and-resource-pools.md` | Thread pools, connection pools, and resource exhaustion |
| `references/` | `resource-efficiency.md` | CPU, memory, IO, and network efficiency review |
| `references/` | `capacity-planning.md` | Headroom estimation, scaling triggers, and quota awareness |
| `references/` | `load-stress-spike-soak-testing.md` | Load test types, design, safety, and pass/fail criteria |
| `checklists/` | `performance-review-checklist.md` | End-to-end performance review checklist |
| `checklists/` | `database-performance-checklist.md` | Database-specific performance checklist |
| `checklists/` | `load-testing-checklist.md` | Load test readiness and execution checklist |
| `checklists/` | `scalability-checklist.md` | Scalability limiter and growth dimension checklist |
| `templates/` | `performance-review.md` | Fill-in-the-blank performance review output |
| `templates/` | `load-test-plan.md` | Load test plan template |
| `templates/` | `scalability-analysis.md` | Scalability analysis template |
| `templates/` | `bottleneck-hypothesis-table.md` | Hypothesis table for bottleneck investigation |
| `templates/` | `capacity-planning-note.md` | Capacity planning note template |
| `templates/` | `cost-performance-tradeoff.md` | Cost vs performance decision template |
| `examples/` | `java-backend-performance-review-example.md` | Java N+1 query pattern review example |
| `examples/` | `java-performance-patterns.md` | Java-specific performance patterns and anti-patterns |
