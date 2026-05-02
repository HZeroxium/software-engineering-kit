---
purpose: Parameterized test candidates and readability guidance
load-when: Many inputs should satisfy the same behavior or validation rule
tier: scenario
see-also: []
---

# Parameterized Tests

## Use Parameterized Tests When

- Same behavior should hold for many inputs.
- Boundary values need coverage.
- Validation rules have many cases.
- Enum/status combinations need coverage.
- Format parsing has many examples.
- Error classification maps multiple inputs to outputs.

## Good Candidates

- Null/empty/blank handling.
- Min/max values.
- Invalid formats.
- Role/status matrices.
- Retryable vs non-retryable errors.
- Permission combinations.
- Input normalization.
- Mapper behavior.

## Good Practices

- Keep each case readable.
- Include case description when useful.
- Avoid hiding complex setup in unreadable argument lists.
- Use parameterized tests for repeated behavior, not unrelated scenarios.
- Ensure each invocation has clear expected result.
- Add separate tests when scenario-specific setup becomes complex.

## Java Notes

When using JUnit Jupiter parameterized tests:

- Use project-supported dependency and conventions.
- Prefer `@CsvSource`, `@MethodSource`, or project-standard source style when readable.
- Use `@MethodSource` for complex objects.
- Keep display names useful when failures occur.
- Do not add new dependencies without approval.
