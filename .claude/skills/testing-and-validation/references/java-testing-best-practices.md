# Java Testing Best Practices

## General

- Prefer behavior-focused tests.
- Keep tests deterministic.
- Use descriptive test names.
- Keep setup readable.
- Avoid excessive mocking.
- Use fixed time through `Clock` or project equivalent.
- Avoid sleeping in tests.
- Avoid relying on execution order.
- Prefer meaningful assertions.
- Add regression tests for bugs.

## Spring / Backend

Check test level carefully:

- Use slice tests when framework layer behavior matters but full app context is unnecessary.
- Use integration tests for repository, transaction, serialization, and security filter behavior.
- Use containerized tests when real database behavior matters.
- Avoid mocking the persistence layer when the bug is in query/transaction behavior.
- Verify error response contracts.
- Verify authorization behavior.
- Verify transaction rollback behavior.

## Transactions

Test:

- Commit behavior.
- Rollback behavior.
- Duplicate writes.
- Constraint violations.
- Events emitted after commit when relevant.
- Cache consistency.
- Idempotent retry behavior.

## Security

Test:

- Unauthenticated request.
- Unauthorized role.
- Wrong owner/tenant.
- Valid authorized request.
- Sensitive fields excluded.
- Invalid token/session if applicable.

## Assertions

Prefer assertions on:

- Returned value.
- Persisted state.
- Published event.
- Error type/status.
- Side effects.
- Interaction with external boundary only when behavior depends on it.

Avoid assertions on:

- Private method calls.
- Incidental internal order.
- Overly broad snapshots.
