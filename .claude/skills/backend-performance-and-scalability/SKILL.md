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

## Workflow

1. Identify user-visible performance goal.
2. Collect existing evidence if available: metrics, traces, logs, profiles, query plans, benchmarks, load tests.
3. If evidence is missing, label bottlenecks as hypotheses.
4. Analyze latency, throughput, tail latency, resource usage, database, cache, concurrency, and external dependencies.
5. Identify scalability limiters and cost-performance trade-offs.
6. Recommend minimal optimizations ranked by evidence and risk.
7. Define validation metrics and load-test plan.
8. Separate facts, assumptions, hypotheses, and unknowns.

## Expected Output

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
