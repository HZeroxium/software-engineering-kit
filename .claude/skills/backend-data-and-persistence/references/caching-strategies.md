---
purpose: Caching patterns, invalidation strategies, TTL, stampede protection, distributed vs local cache trade-offs
load-when: Designing or reviewing cache behavior, invalidation logic, or cache correctness
tier: domain
see-also:
  - multi-tenancy-data-isolation.md
---

# Caching Strategies

## Purpose

Use cache to improve latency or reduce load without breaking correctness.

## Strategies

- Cache-aside.
- Write-through.
- Write-behind.
- Read-through.
- TTL-based.
- Event-driven invalidation.
- Local in-memory cache.
- Distributed cache.

## Questions

- What is the source of truth?
- Can stale data be tolerated?
- How is cache invalidated?
- Is authorization-dependent data cached?
- Does key include tenant/user context?
- What happens if cache is down?
- Is stampede protection needed?

## Smells

- Cache without invalidation.
- Sensitive data cached without controls.
- Tenant/user missing from key.
- Cache returns data caller no longer has access to.
- Cache outage causes full system outage.
