---
purpose: Core evidence, hypothesis, experiment, root-cause, minimal-fix, regression-test, and validation workflow
load-when: Starting any non-trivial debugging task
tier: foundational
see-also:
  - stack-trace-analysis.md
  - logs-metrics-traces-debugging.md
  - ci-failure-debugging.md
  - concurrency-debugging.md
  - timeout-retry-idempotency-debugging.md
---

# Evidence-Based Debugging

## Principle

Do not jump from symptom to fix. Move through:

1. Evidence.
2. Facts.
3. Hypotheses.
4. Experiments.
5. Root cause.
6. Minimal fix.
7. Regression test.
8. Validation.

## Evidence

Useful evidence includes:

- Exact error message.
- Full stack trace.
- Failing test output.
- Logs around the failure.
- Metrics.
- Traces.
- Recent diffs.
- Config changes.
- Dependency changes.
- Environment differences.
- Reproduction steps.

## Facts vs Assumptions vs Hypotheses

Facts:

- Directly observed in code, logs, tests, configs, or output.

Assumptions:

- Plausible but not yet proven.

Hypotheses:

- Testable explanations for the failure.

Do not present hypotheses as root cause until confirmed.

## Good Experiments

A good experiment:

- Tests one hypothesis.
- Has expected result.
- Is narrow.
- Is repeatable.
- Produces interpretable output.
- Does not mutate high-risk systems without approval.

## Minimal Fix

A minimal fix:

- Addresses the confirmed root cause.
- Avoids unrelated refactors.
- Preserves existing style.
- Includes a regression test when practical.
- Has clear validation.

## Stop Conditions

Stop and escalate when:

- Production data may be corrupted.
- Security is involved.
- Root cause is unclear.
- Experiments require high-risk operations.
- Blast radius is unknown.
- The fix would require migration, infrastructure, CI/CD, or auth/security changes.
