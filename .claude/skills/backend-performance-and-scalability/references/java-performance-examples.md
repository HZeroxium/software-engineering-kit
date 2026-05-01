# Java Performance Examples

Examples are illustrative only. Follow repository conventions.

## Bounded Executor Concept

```java
public record WorkerPoolConfig(
    int maxThreads,
    int queueCapacity
) {}
```

## Avoid Repeated Calls in Loop

```java
// Risk: repeated remote or DB calls inside a loop.
for (OrderId id : orderIds) {
    Order order = orders.get(id);
}
```

Prefer batch access when repository conventions support it.

## Tail Latency Review

```text
Measure:
- p50, p95, p99 request latency
- DB query latency
- external call latency
- thread/connection pool saturation
```

## Notes

- Do not assume JVM flags or framework tuning.
- Validate with measurements.
- Avoid micro-optimizations before finding bottleneck.
