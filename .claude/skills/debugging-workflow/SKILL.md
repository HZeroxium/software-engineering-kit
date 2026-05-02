---
name: debugging-workflow
description: Use when investigating concrete failures such as errors, exceptions, failing tests, stack traces, logs, CI failures, runtime or production symptoms, performance regressions, timeouts, retries, race conditions, flaky behavior, or unexplained behavior. Do not use for general implementation planning, pure code review, or documentation-only tasks.
---

# Debugging Workflow

## Purpose

Debug failures deeply using evidence, not guesswork.

This Skill is instruction-only. It does not enforce behavior, run hooks, configure MCP, restrict tools, or define repo-specific commands.

## When to use

Use this Skill when the user provides or asks about:

- Error message.
- Exception.
- Stack trace.
- Failing test.
- CI failure.
- Logs.
- Runtime symptom.
- Production symptom.
- Performance regression.
- Timeout.
- Retry issue.
- Race condition.
- Flaky behavior.
- Unexplained behavior.

## When not to use

Do not use this Skill for:

- General implementation planning without a failure.
- Code review unless reviewing a suspected fix.
- Requirements analysis.
- Documentation-only tasks.
- Guessing root cause without evidence.

## Required inputs

Useful inputs include:

- Expected behavior.
- Actual behavior.
- Full error message.
- Stack trace.
- Logs.
- Failing test output.
- CI output.
- Reproduction steps.
- Recent changes.
- Relevant files.
- Environment details.
- Input data.
- Config differences.
- Metrics or traces.

## Workflow

1. Capture expected vs actual behavior.
2. Summarize evidence.
3. Separate facts, assumptions, and hypotheses.
4. Build ranked hypotheses.
5. Design experiments to confirm or reject each hypothesis.
6. Inspect relevant repo files and configs before proposing implementation changes.
7. Identify root cause only when supported by evidence.
8. Propose minimal fix plan.
9. Add or recommend regression test.
10. Discover validation commands from the current repo.
11. Validate with narrowest checks first, then broader checks.
12. Summarize remaining unknowns.

## Expected Outputs

Output type: `analysis` - diagnostic reasoning with evidence, hypotheses, experiments, supported root cause, minimal fix direction, regression test, and validation plan.

Default output:

```markdown
# Expected vs Actual

# Evidence Summary

# Confirmed Facts

# Assumptions

# Ranked Hypotheses

# Experiments

# Root Cause

# Minimal Fix Plan

# Regression Test

# Validation Plan

# Remaining Unknowns
```

If root cause is not confirmed, say so and keep it as a hypothesis.

## Rule coordination

This Skill provides task-specific debugging procedure and supporting references. Global safety, context, validation, and output rules still apply from:

- `.claude/rules/10-safety-and-permissions.md`
- `.claude/rules/20-context-engineering.md`
- `.claude/rules/40-harness-engineering-and-validation.md`
- `.claude/rules/50-output-standards.md`

## Safety boundaries

- Do not invent commands, APIs, framework behavior, file paths, dependency versions, or test results.
- Inspect the repo before deciding commands or implementation approach.
- Redact sensitive values before summarizing logs.
- Prefer read-only exploration until the root cause and scope are clear.

## Validation

Use applicable validation:

- Reproduction.
- Targeted failing test.
- Regression test.
- Build.
- Typecheck.
- Lint.
- Static analysis.
- CI.
- Logs.
- Metrics.
- Traces.
- Profiling.
- Manual review.

- Do not invent verification commands. Discover them from repo evidence.

## Failure handling

If debugging stalls:

- State what is known.
- State what is unknown.
- Identify the next smallest experiment.
- Avoid broad speculative fixes.
- Escalate if production impact, security impact, data corruption, or unclear blast radius exists.

## Supporting files

Load only when useful:

### Navigation

- `references/reference-index.md` - Load first when multiple references may apply or when unsure which supporting file to use.

### References

- `references/evidence-based-debugging.md` - Core evidence-to-root-cause workflow.
- `references/stack-trace-analysis.md` - Exceptions and stack traces.
- `references/logs-metrics-traces-debugging.md` - Logs, metrics, traces, and observability signals.
- `references/ci-failure-debugging.md` - CI job, build, and pipeline failures.
- `references/concurrency-debugging.md` - Races, deadlocks, duplicate writes, and flaky/order-dependent behavior.
- `references/timeout-retry-idempotency-debugging.md` - Timeouts, retries, retry storms, duplicate side effects, and idempotency gaps.

### Checklists and templates

- `checklists/debugging-checklist.md` - Load before summarizing or when audit completeness matters.
- `checklists/before-fix-checklist.md` - Load before bug-fix edits.
- `templates/debug-report.md` - Use for a full debugging analysis.
- `templates/hypothesis-table.md` - Use for ranked hypotheses.
- `templates/reproduction-steps.md` - Use to capture reproducibility.
- `templates/root-cause-analysis.md` - Use for incident or failure RCA.
- `templates/regression-test-after-fix.md` - Use after confirmed fix direction.
