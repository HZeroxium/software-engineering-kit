---
purpose: Database bottleneck analysis — queries, indexes, N+1, pagination, lock contention, connection pools
load-when: Task involves database queries, slow queries, missing indexes, N+1 patterns, or DB connection limits
tier: domain
see-also:
  - concurrency-and-resource-pools.md
---

# Database Performance

## Purpose

Analyze database bottlenecks in backend workflows.

## Review Areas

- Query filters.
- Sorts.
- Joins.
- Pagination.
- Indexes.
- N+1 queries.
- Lock contention.
- Transaction duration.
- Connection pool usage.
- Read/write split if present.

## Questions

- Does query use selective filters?
- Does index support filter and sort?
- Is result size bounded?
- Is pagination efficient?
- Is tenant/user predicate included?
- Does transaction hold locks too long?
- Are queries repeated in a loop?

## Failure Modes

- Full table scan.
- Deep offset pagination.
- N+1 query pattern.
- Missing index.
- Hot row/partition.
- Long transaction blocking writes.
