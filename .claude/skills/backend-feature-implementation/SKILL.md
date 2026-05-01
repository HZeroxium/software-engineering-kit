---
name: backend-feature-implementation
description: Framework-agnostic backend implementation workflow. Use after design is sufficiently clear to explore repository evidence, plan small reviewable backend changes, edit safely, discover validation commands, run checks when appropriate, fix failures, and summarize residual risk.
---

# Backend Feature Implementation

Use this Skill when the user asks to implement backend code, modify backend behavior, add tests, refactor backend logic, or complete backend task execution.

This Skill assumes design is sufficiently clear. If design is unclear, use `backend-feature-design` first.

## Purpose

Guide backend implementation through:

```text
explore -> plan -> edit -> test -> fix-loop -> summarize
```

## Activation Criteria

Use when implementation affects:

- Backend APIs or interfaces.
- Use-case/application logic.
- Domain/business rules.
- Data/persistence.
- Integrations.
- Reliability/resilience.
- Observability/operations.
- Tests and validation.
- Backend refactoring.

## Non-Goals

Do not:

- Start editing before understanding repo conventions.
- Invent APIs, commands, internal library behavior, or framework behavior.
- Assume Spring or any Java framework.
- Perform broad rewrites without explicit user request.
- Modify high-risk areas without approval.
- Claim tests passed unless they were run and results are known.

## Safety Boundaries

Ask for confirmation before:

- Migrations.
- Auth/security changes.
- CI/CD changes.
- Production config changes.
- Destructive commands.
- Dependency upgrades.
- Generated code updates.
- Broad rewrites.
- Secret handling.
- External system writes.

## Workflow

1. **Explore read-only**
   - Identify affected files/modules.
   - Read nearby code, tests, configs, and build files.
   - Discover repo conventions and validation commands from evidence.

2. **Plan**
   - Produce minimal implementation plan.
   - Identify tests to add/update.
   - Identify risks and approval gates.

3. **Edit**
   - Make small, focused, reviewable changes.
   - Preserve existing style and public contracts unless behavior change is explicit.
   - Reuse existing abstractions and internal wrappers.

4. **Validate**
   - Run discovered build/test/typecheck/lint/static analysis commands when safe and requested/appropriate.
   - If unable to run, state why and provide commands.

5. **Fix Loop**
   - Analyze failures.
   - Apply minimal fixes.
   - Re-run relevant checks when feasible.

6. **Summarize**
   - Report files changed, behavior changed, validation run, failures, residual risks, and follow-ups.

## Evidence Rules

- Separate facts, assumptions, and hypotheses.
- Cite repository evidence in summaries when possible.
- Do not claim conventions unless seen in code/config/tests.
- Do not invent validation commands.

## Expected Output

Use these templates when useful:

- `templates/backend-implementation-plan.md`
- `templates/backend-task-breakdown.md`
- `templates/backend-implementation-summary.md`
- `templates/backend-validation-report.md`
- `templates/backend-exit-criteria.md`

## Final Response Shape

```text
# Backend Implementation Summary

## Exploration Summary
...

## Affected Files / Modules
...

## Implementation Plan
...

## Changes Made
...

## Validation
...

## Tests Run / Not Run
...

## Residual Risks
...

## Next Recommended Step
...
```
