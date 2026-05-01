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
