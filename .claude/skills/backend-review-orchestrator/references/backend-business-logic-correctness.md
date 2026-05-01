# Backend Business Logic Correctness

## Review Questions

- Does the code implement the requested behavior?
- Are business invariants enforced?
- Are invalid state transitions blocked?
- Are edge cases covered?
- Are errors mapped correctly?
- Can internal flows bypass validation?
- Does persistence enforce critical uniqueness/constraints?
- Are side effects safe and ordered correctly?

## Java-Oriented Signals

Look for:

- Use-case/service methods.
- Domain model methods.
- Repository calls.
- Transaction boundaries.
- Exception mapping.
- State enums.
- Validation objects.
- Tests for domain behavior.

Do not assume Spring annotations or framework transactions unless repo evidence confirms them.

## Common Bugs

- Null/empty edge cases.
- Wrong ownership check.
- Missing idempotency.
- Incorrect status transition.
- Lost update.
- Race condition.
- Error swallowed.
- Event emitted before durable state.
- Tests asserting implementation instead of behavior.
