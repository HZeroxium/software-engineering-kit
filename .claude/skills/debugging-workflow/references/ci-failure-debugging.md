# CI Failure Debugging

## First Questions

- Which job failed?
- Which step failed?
- What command ran?
- Did the same command fail locally?
- Is failure deterministic or flaky?
- Did code change or environment change?
- Did dependencies change?
- Did cache state change?

## Evidence to Inspect

- CI job name.
- Failing command.
- Full error output.
- Test reports.
- Build logs.
- Dependency resolution logs.
- Changed files.
- Recent commits.
- CI config.
- Cache config.
- Environment variables names, not secret values.
- Docker image version.
- Runtime version.

## Common Causes

- Code regression.
- Test expectation outdated.
- Missing dependency.
- Version mismatch.
- Generated files out of date.
- Flaky test.
- Race condition.
- Timeout.
- Environment difference.
- Cache corruption.
- Missing secret or config.
- External dependency unavailable.

## Classification

Classify failure as:

- Code issue.
- Test issue.
- Environment issue.
- CI infrastructure issue.
- Flaky/unclear.

## Fix Strategy

- Reproduce locally when possible.
- Run narrow failing command.
- Inspect recent changes.
- Avoid changing tests unless expectation is wrong.
- Avoid retry-only “fixes” without understanding.
- Add regression test if code bug.
- Improve diagnostics if failure is unclear.
