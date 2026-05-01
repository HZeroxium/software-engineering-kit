# Backend Skill Handoff

## Selected Skill

`<specialized backend Skill name>`

## Why This Skill

`<reason the selected Skill is the best next step>`

## Task Summary

`<one-sentence task summary>`

## Primary Backend Scope

`<primary scope>`

## Secondary Backend Scopes

- `<scope>`
- `<scope>`

## Known Context

- `<context>`
- `<context>`

## Assumptions

- `<assumption>`
- `<assumption>`

## Unknowns

- `<unknown>`
- `<unknown>`

## Risks to Preserve

- `<risk>`
- `<risk>`

## Constraints

- Framework-agnostic unless repo evidence confirms a framework.
- Vendor-agnostic and cloud-agnostic unless explicitly specified.
- Java examples are acceptable, but do not assume Spring or any Java framework.
- Do not invent internal library behavior.
- Prefer repo evidence over conventions.
- Preserve human approval for high-risk areas.

## Handoff Prompt

```text
Use the <selected backend Skill> Skill.

Task:
<task summary>

Primary scope:
<primary backend scope>

Secondary scopes:
<secondary scopes>

Known context:
<known context>

Assumptions:
<assumptions>

Unknowns:
<unknowns>

Risks:
<risks>

Constraints:
- Remain framework-agnostic unless evidence confirms a framework.
- Do not assume Spring, FastAPI, NestJS, cloud provider, vendor platform, or internal library behavior.
- Use Java examples only when helpful.
- Identify security, data, reliability, performance, observability, operations, testing, governance, and AI risks where relevant.

Expected output:
<design / implementation plan / review triage / test strategy / risk analysis>
```
