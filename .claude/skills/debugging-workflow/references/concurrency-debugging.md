---
purpose: Race condition, deadlock, duplicate write, lost update, and order-dependent failure analysis
load-when: Debugging flaky behavior, races, deadlocks, duplicate records, inconsistent state, or order-dependent failures
tier: scenario
see-also: []
---

# Concurrency Debugging

## Symptoms

- Flaky tests.
- Duplicate records.
- Lost updates.
- Deadlocks.
- Timeouts under load.
- Inconsistent state.
- Occasional null/invalid state.
- Order-dependent failures.
- Works locally but fails in CI.
- Rare production incidents.

## Evidence

Collect:

- Thread dumps.
- Stack traces.
- Timestamps.
- Transaction logs.
- Lock wait information.
- Retry logs.
- Duplicate request IDs.
- Correlation IDs.
- Database isolation level.
- Message offsets.
- Queue redelivery information.

## Hypotheses

Common hypotheses:

- Race condition.
- Missing lock.
- Wrong lock scope.
- Lost update.
- Unsafe shared mutable state.
- Non-idempotent retry.
- Transaction boundary issue.
- Event emitted before commit.
- Duplicate message consumption.
- Thread pool starvation.
- Deadlock.
- Connection pool exhaustion.

## Experiments

- Add deterministic test with concurrent execution.
- Reproduce with repeated runs.
- Inspect DB constraints.
- Inspect transaction annotations.
- Inspect lock ordering.
- Inspect retry behavior.
- Inspect idempotency key handling.
- Inspect resource pool metrics.
- Review thread dumps.

## Fix Patterns

- Add idempotency.
- Add unique constraint.
- Use optimistic locking.
- Narrow transaction boundaries.
- Move event emission after commit.
- Protect shared state.
- Bound retries.
- Add timeout.
- Avoid blocking event-loop threads.
