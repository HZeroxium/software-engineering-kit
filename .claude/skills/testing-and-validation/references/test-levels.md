---
purpose: Test level taxonomy and selection rule for choosing the narrowest useful validation
load-when: Deciding which test level can prove the behavior
tier: foundational
see-also:
  - unit-testing.md
  - integration-testing.md
  - system-testing.md
  - contract-testing.md
  - regression-testing.md
  - java-testing-best-practices.md
---

# Test Levels

## Unit Tests

Use for:

- Pure functions.
- Domain rules.
- Validation logic.
- Mapping logic.
- Error classification.
- Small service logic with mocked boundaries.

Strengths:

- Fast.
- Deterministic.
- Easy to localize failures.

Limitations:

- Can miss integration issues.
- Can over-mock reality.

## Integration Tests

Use for:

- Database behavior.
- Repository queries.
- Transactions.
- Serialization/deserialization.
- Framework wiring.
- External client adapters with fake/container dependency.

Strengths:

- Catches wiring and persistence issues.
- Validates real framework behavior.

Limitations:

- Slower.
- Requires environment management.

## System Tests

Use for:

- End-to-end user or service flows.
- Cross-module behavior.
- Deployment-like scenarios.
- Critical business workflows.

Strengths:

- Highest confidence for full flow.

Limitations:

- Slower.
- Harder to debug.
- More fragile if overused.

## Contract Tests

Use for:

- Provider/consumer API compatibility.
- External service integration.
- Event schemas.
- Backward compatibility.

Strengths:

- Prevents integration breakage.

Limitations:

- Requires clear contracts and versioning.

## Regression Tests

Use for:

- Bugs that were fixed.
- Production incidents.
- Recurrent failure modes.
- Critical edge cases.

Strengths:

- Prevents recurrence.

Limitations:

- Must target root cause, not incidental behavior.

## Selection Rule

Prefer the lowest test level that can prove the behavior.

Escalate to broader tests when:

- Framework behavior matters.
- Database behavior matters.
- Serialization or API contract matters.
- Integration boundary matters.
- Prior bug escaped lower-level tests.
