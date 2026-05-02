# Rule Design Example

## User Request

"I always forget to mention edge cases when reviewing code. Should I add a global rule, or create a Skill?"

## Analysis

- Domain: code review communication behavior.
- Frequency: every code review session — stable, recurring.
- Nature: persistent global preference, not a multi-step procedure.
- Complexity: one bullet in an existing rule; no checklists, templates, or examples needed.
- Target tool: Claude Code (user-global).
- Artifact type: Rule, not Skill.
- Reason: the request is a communication preference that applies to all code review regardless of domain. It has no branching workflow, no reusable template, and no progressive context loading benefit. A single bullet added to `50-output-standards.md` under the code review section is sufficient.

## Recommendation

Add to the existing `~/.claude/rules/50-output-standards.md` under the relevant code review section:

```text
- Explicitly call out edge cases, boundary conditions, and failure modes for changed behavior.
```

Defer:

- Skill, until edge case analysis becomes a structured multi-step procedure with domain-specific checklists and a reusable severity model.
- Agent, until edge case analysis requires separate context or automated invocation.

## Rule Location

`~/.claude/rules/50-output-standards.md` — existing rule; append one bullet to the code review section.

## When to Promote to Skill

Promote to a Skill when one or more of the following becomes true:

- Edge case analysis requires domain-specific checklists (e.g., one checklist for API changes, a separate one for data mutations).
- A reusable severity model for edge case findings is needed across multiple review contexts.
- The edge case workflow has enough stable structure to benefit from templates or worked examples.
- The behavior needs to be independently triggerable via `/edge-case-review` rather than always active.

## Validation

- Invoke a code review task (e.g., "Review this diff").
- Confirm the output includes an explicit edge case or boundary condition section.
- Check for duplication with any existing edge-case or failure-mode guidance in `50-output-standards.md` or `00-personal-preferences.md`.
- Confirm the new bullet does not conflict with existing review guidance.
