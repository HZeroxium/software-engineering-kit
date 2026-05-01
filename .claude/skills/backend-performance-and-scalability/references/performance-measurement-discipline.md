# Performance Measurement Discipline

## Principle

Measure before optimizing. If measurement is unavailable, label conclusions as hypotheses.

## Measurement Sources

- Metrics.
- Traces.
- Logs.
- Query plans.
- Profilers.
- Benchmarks.
- Load tests.
- Resource dashboards.
- CI performance checks.

## Workflow

```text
Measure -> Hypothesize -> Optimize minimally -> Validate -> Monitor regression
```

## Anti-Patterns

- Optimizing from intuition only.
- Using average latency only.
- Benchmarking unrealistic data.
- Ignoring GC/resource effects.
- Optimizing rare paths while hot path remains slow.
- No regression check after optimization.
