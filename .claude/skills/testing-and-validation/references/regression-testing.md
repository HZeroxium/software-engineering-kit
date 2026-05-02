---
purpose: Regression test purpose, triggers, quality bar, and output expectations
load-when: Fixing a bug, incident, escaped defect, or recurring edge case
tier: domain
see-also: []
---

# Regression Testing

## Purpose

A regression test proves that a known bug or high-risk behavior does not return.

## When to Add

Add a regression test when:

- Fixing a bug.
- Reproducing a production incident.
- Changing critical business logic.
- Changing auth/security.
- Changing data consistency logic.
- Changing retry/idempotency behavior.
- Changing edge-case handling.
- Fixing a concurrency issue.

## Good Regression Test

A good regression test:

- Fails before the fix.
- Passes after the fix.
- Targets the root cause.
- Uses the narrowest appropriate test level.
- Has clear test data.
- Has meaningful assertions.
- Avoids incidental implementation details.

## Anti-Patterns

- Test only checks that no exception is thrown.
- Test reproduces setup but not the actual failure.
- Test asserts implementation details instead of behavior.
- Test is too broad and slow.
- Test depends on time, randomness, or ordering without control.
- Test uses unrealistic data that misses the original bug.

## Output

When proposing a regression test, state:

- Bug/risk.
- Root cause or hypothesis.
- Test level.
- Scenario.
- Expected failure before fix.
- Expected pass after fix.
- Command to run if discovered from repo.
