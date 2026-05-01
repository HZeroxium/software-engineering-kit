# Caching Performance

## Purpose

Use caching to improve performance only when correctness remains clear.

## Questions

- What is the source of truth?
- What latency/load reduction is expected?
- What is the cache key?
- Can data be stale?
- How is cache invalidated?
- Is authorization-dependent data cached?
- What happens on cache miss or cache outage?

## Performance Risks

- Cache stampede.
- Low hit rate.
- Serialization overhead.
- Cache network latency exceeds benefit.
- Memory pressure.
- Over-caching rarely used data.

## Correctness Risks

- Stale data.
- Cross-tenant data leakage.
- Serving data after permission changes.
- Missing invalidation on write.
