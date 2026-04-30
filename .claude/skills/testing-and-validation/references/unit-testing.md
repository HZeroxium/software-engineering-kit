# Unit Testing

## Use Unit Tests For

- Business rules.
- Validation logic.
- Calculations.
- State transition rules.
- Mapping logic.
- Error classification.
- Retry decision logic.
- Idempotency decision logic.

## Good Unit Test Traits

- Fast.
- Deterministic.
- Focused on one behavior.
- Clear setup.
- Clear assertion.
- No external network.
- No real database unless the project treats it as lightweight local test.
- Descriptive test name.
- Meaningful failure message.

## Avoid

- Testing implementation details.
- Mocking every internal method.
- Weak assertions such as only checking non-null.
- Tests that pass even when behavior is wrong.
- Overly broad tests that fail for many reasons.
- Time-dependent tests without controlling time.
- Randomness without deterministic seed.
- Hidden dependency on test execution order.

## Structure

Prefer Arrange / Act / Assert:

- Arrange: build input and dependencies.
- Act: execute behavior.
- Assert: verify meaningful outcome and side effects.

## Java Notes

For Java backend code, consider:

- JUnit Jupiter.
- AssertJ or project-standard assertion library.
- Mockito only at boundaries where a real dependency is not appropriate.
- Fixed `Clock` for time-sensitive logic.
- Explicit test names describing behavior.
