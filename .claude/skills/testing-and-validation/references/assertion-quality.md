---
purpose: Strong vs weak assertions and guidance for diagnosable test failures
load-when: Reviewing assertion strength or improving brittle or low-signal tests
tier: scenario
see-also: []
---

# Assertion Quality

## Good Assertions

Good assertions verify meaningful behavior:

- Returned value is correct.
- Error status/type/message is correct.
- Persisted state is correct.
- Event/message is published once.
- Sensitive field is absent.
- Unauthorized request is denied.
- Duplicate request is idempotent.
- Retry behavior is bounded.
- Side effect happens or does not happen as expected.

## Weak Assertions

Avoid relying only on:

- Not null.
- No exception thrown.
- Method called once without verifying outcome.
- Snapshot of unrelated data.
- Exact private implementation order.
- Broad object equality when only one field matters.
- Logging assertion as the only proof of behavior.

## Failure Messages

A good test failure should reveal:

- Scenario.
- Expected behavior.
- Actual behavior.
- Relevant input.
- Broken invariant.

## Assertion Scope

Assert enough to prove behavior, but not so much that the test becomes brittle.

## Negative Assertions

Use negative assertions for:

- Sensitive data not returned.
- Unauthorized action not allowed.
- Duplicate side effect not produced.
- Invalid input not persisted.
- Event not emitted on failure.
