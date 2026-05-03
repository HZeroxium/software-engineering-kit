---
purpose: Concurrency safety and resource pool sizing — thread pools, connection pools, locks, backpressure, and exhaustion failure modes
load-when: Task involves concurrency, thread contention, connection pool limits, or queue consumer design
tier: domain
see-also:
  - resource-efficiency.md
---

# Concurrency and Resource Pools

## Purpose

Avoid resource exhaustion and concurrency bugs.

## Review Areas

- Thread pools.
- Connection pools.
- Async executors.
- Worker concurrency.
- Queue consumers.
- Locks.
- Rate limits.
- Backpressure.

## Questions

- Is concurrency bounded?
- Which resource pool saturates first?
- Are blocking calls made on limited threads?
- Are DB connections sufficient but bounded?
- Are locks held during IO?
- Is work canceled when caller times out?

## Failure Modes

- Thread starvation.
- Connection pool exhaustion.
- Unbounded queue growth.
- Lock contention.
- Deadlock.
- Retry storm consuming all workers.
