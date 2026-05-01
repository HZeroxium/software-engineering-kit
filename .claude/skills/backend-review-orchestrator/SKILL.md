---
name: backend-review-orchestrator
description: Backend review orchestration workflow. Use for backend PRs, diffs, designs, or AI-generated code to classify affected backend scopes, route review focus, produce severity-based findings, recommend minimal fixes, and define validation methods.
---

# Backend Review Orchestrator

Use this Skill when reviewing backend code, diffs, PRs, designs, or AI-generated backend implementation.

This Skill orchestrates review across backend scopes. It does not duplicate every specialized backend checklist.

## Purpose

Produce a severity-based backend review report that identifies:

- Blocking issues.
- Important issues.
- Optional improvements.
- Affected backend scopes.
- Affected files/modules.
- Why each issue matters.
- Failure mode.
- Minimal fix recommendation.
- Test/validation method.
- Remaining risks.

## Activation Criteria

Use when:

- Reviewing backend code/diff/PR/design.
- Reviewing AI-generated backend code.
- Performing pre-merge backend review.
- Backend risk spans multiple areas.
- The user asks for backend review triage or review orchestration.

## Non-Goals

Do not:

- Rewrite the whole implementation.
- Duplicate all specialized review checklists.
- Assume framework behavior without evidence.
- Invent internal library APIs.
- Treat style-only issues as blocking unless they cause real risk.
- Approve code without validation evidence.

## Review Scopes

Classify findings by:

- Domain/API.
- Application architecture.
- Data/persistence.
- Security/trust.
- Integration/distributed communication.
- Reliability/resilience.
- Performance/scalability.
- Observability/operations.
- AI/governance/quality.

## Severity Model

- **Blocking:** Must fix before merge. Correctness, security, data loss, migration safety, production outage, contract break, or severe operational risk.
- **Important:** Should fix before merge or track explicitly. Meaningful maintainability, test, observability, performance, or reliability risk.
- **Optional:** Useful improvement, cleanup, naming, readability, or non-blocking refactor.

## Workflow

1. Identify review target and context.
2. Classify affected backend scopes.
3. Inspect behavior, contracts, data, security, integrations, reliability, performance, observability, tests, and operations.
4. Prioritize findings by production risk.
5. Recommend minimal fixes.
6. Define validation method.
7. Produce final backend review report.
8. If needed, hand off to specialized backend Skill.

## Evidence Rules

- Distinguish facts, assumptions, and hypotheses.
- Tie findings to code/design evidence.
- Prefer minimal fix recommendations.
- Require validation via tests/build/typecheck/lint/static analysis/CI/logs/metrics/manual review where applicable.
- If context is missing, say what is needed.

## Expected Output

Use these templates when useful:

- `templates/backend-review-report.md`
- `templates/backend-scope-review-matrix.md`
- `templates/backend-minimal-fix-plan.md`
- `templates/backend-review-handoff.md`

## Final Response Shape

```text
# Backend Review Report

## Summary
...

## Scope Classification
...

## Blocking Findings
...

## Important Findings
...

## Optional Findings
...

## Minimal Fix Plan
...

## Validation Recommendations
...

## Remaining Risks
...
```
