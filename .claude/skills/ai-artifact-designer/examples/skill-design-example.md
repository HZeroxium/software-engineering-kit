# Skill Design Example

## User Request

“I often ask Claude to review AI-generated code before accepting it. Should I make a Skill?”

## Analysis

- Domain: code review.
- Frequency: high.
- Risk: medium to high.
- Target tool: Claude Code.
- Artifact type: Skill.
- Reason: repeated workflow with clear trigger, reusable severity model, checklists, templates, and validation expectations.

## Recommendation

Create:

```text
~/.claude/skills/code-review/
  SKILL.md
  templates/
    severity-review-report.md
  references/
    review-priority-model.md
  checklists/
    ai-generated-code-review-checklist.md
```

Defer:

- Agent, until code review volume becomes large enough to benefit from separate context.
- Hook, until there is a real need to block commands or edits.
- MCP, because no live external data is required.

## Skill Purpose

Review code, diffs, PRs, and AI-generated patches using severity-based production review.

## Activation Criteria

Use when reviewing:

- Diffs.
- Pull requests.
- AI-generated patches.
- Implementation plans.

Do not use as the main implementation workflow.

## Validation

- Invoke /code-review on a small pseudo diff.
- Confirm findings are severity-ranked.
- Confirm it recommends minimal fixes.
- Confirm it does not invent repo commands.
