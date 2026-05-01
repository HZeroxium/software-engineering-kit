# Backend Analysis Summary

## Summary

`<concise backend analysis result>`

## Classification

- **Task type:** `<task type>`
- **Primary scope:** `<scope>`
- **Secondary scopes:** `<scopes>`
- **Risk level:** `<low/medium/high/critical>`
- **Recommended next Skill:** `<skill or none>`

## Backend Reasoning

### What the task is really about

`<explain the core backend concern behind the user request>`

### Why this scope matters

`<explain why the selected scope is the right lens>`

### What not to assume

- Do not assume `<framework/platform/library behavior>`.
- Do not assume `<data model/API/runtime behavior>`.
- Do not assume `<internal library behavior>`.

## Key Design Questions

1. `<question>`
2. `<question>`
3. `<question>`

## Risks

| Risk     | Scope     | Severity                     | Mitigation     |
| -------- | --------- | ---------------------------- | -------------- |
| `<risk>` | `<scope>` | `<low/medium/high/critical>` | `<mitigation>` |

## Context Needed Before Implementation

- `<repo files or docs>`
- `<API contract or schema>`
- `<logs, metrics, traces, or failure evidence>`
- `<validation commands>`
- `<business rule clarification>`

## Suggested Next Action

`<single concrete next action>`

## Handoff Prompt

```text
Use the <selected-skill> Skill.

Task:
<task summary>

Primary backend scope:
<scope>

Secondary scopes:
<scopes>

Known context:
<context>

Risks to consider:
<risks>

Do not assume:
<assumptions to avoid>

Expected output:
<design / plan / review triage / implementation plan / test strategy>
```
