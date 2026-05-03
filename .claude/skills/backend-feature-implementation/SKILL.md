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

## Required Inputs

Use available context first. Ask for missing context only when it materially affects implementation safety or scope.

**Required:**
- User request or task description.

**Strongly recommended:**
- Design output from `backend-feature-design` (if design was performed).
- Relevant source files and test files.
- Build files or package manager files.

**Useful when available:**
- Acceptance criteria or issue description.
- Current diffs or recent changes.
- Logs, CI output, or stack traces.
- Config files or schema files.
- Internal library conventions confirmed from the repo.
- Validation commands discovered from README, CI, or build files.
- Risk tolerance and deployment constraints.

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

## Expected Outputs

Output type: **mixed** — this Skill produces different output types across phases:

- **plan** — explore and plan phases: exploration summary, affected files, strategy, test plan, validation commands, risk gates. Use `templates/backend-implementation-plan.md` or `templates/backend-task-breakdown.md`.
- **summary** — summarize phase: files changed, behavior changed, tests added, validation run, failures, residual risks, follow-ups. Use `templates/backend-implementation-summary.md`.
- **report** — when validation is detailed enough to stand alone. Use `templates/backend-validation-report.md`.
- **checklist** — when evaluating readiness before editing or before summarizing. Use `templates/backend-exit-criteria.md`.

For simple low-risk tasks, compress plan and summary into a single response while preserving validation and risk reporting.

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

## Supporting files

Load only when useful. Start with `references/reference-index.md` when the task is broad or multiple references may apply.

| File | Purpose | Load when |
| --- | --- | --- |
| `references/reference-index.md` | Semantic navigation graph for all references, checklists, templates, and examples | Starting a broad task or unsure which reference to load first |
| `references/backend-implementation-workflow.md` | Phase workflow with entry/exit criteria, decision heuristics, and common pitfalls | Starting any backend implementation task |
| `references/test-first-or-test-aware-implementation.md` | Test sequencing rules; test type selection matrix | Deciding when to write tests first; selecting the right test type for a change |
| `references/minimal-reviewable-diffs.md` | Diff scope discipline and split-change criteria | Planning edit scope; noticing the planned change is growing large |
| `references/backend-failure-handling-during-implementation.md` | Failure classification and structured failure report | A check, build, or test has failed during implementation |
| `references/backend-doc-update-during-implementation.md` | Doc update decision criteria | Implementation changes a public contract, error model, config, or operational behavior |
| `templates/backend-implementation-plan.md` | Implementation plan template | Producing a structured implementation plan |
| `templates/backend-task-breakdown.md` | Task breakdown template | Splitting work into parallel or sequential tasks |
| `templates/backend-implementation-summary.md` | Implementation summary template | Producing the final summary |
| `templates/backend-validation-report.md` | Validation report template | Producing a standalone validation report |
| `templates/backend-exit-criteria.md` | Exit criteria checklist | Evaluating implementation readiness |
| `checklists/before-backend-edit-checklist.md` | Pre-edit gate checklist | Before making any backend edit |
| `checklists/backend-risk-gate-checklist.md` | Risk gate checklist | During planning when risky areas may be touched |
| `checklists/backend-implementation-done-checklist.md` | Post-implementation completeness check | Before producing the final summary |
| `examples/java-backend-implementation-plan-example.md` | Filled-in plan example | Calibrating plan depth or format |
