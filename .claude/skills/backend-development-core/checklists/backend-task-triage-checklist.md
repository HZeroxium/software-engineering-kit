# Backend Task Triage Checklist

## Task Understanding

- [ ] Restate the task in one sentence.
- [ ] Identify whether the task is design, implementation planning, review triage, debugging, optimization, operations, or governance.
- [ ] Identify the business capability involved.
- [ ] Identify known technology constraints.
- [ ] Identify unknown repository/framework/internal-library constraints.

## Scope Selection

- [ ] Select one primary 9-scope backend category.
- [ ] Select secondary categories if cross-cutting.
- [ ] Map to the 15-scope model if deeper analysis is needed.
- [ ] Identify whether project onboarding is needed first.

## Context Needed

- [ ] Existing code or repository map.
- [ ] API contract.
- [ ] Domain rules.
- [ ] Data schema.
- [ ] Logs/metrics/traces.
- [ ] Build/test commands.
- [ ] CI/CD or deployment context.
- [ ] Security model.
- [ ] Internal library usage examples.
- [ ] Business constraints.

## Assumption Control

- [ ] Do not assume framework behavior.
- [ ] Do not assume Spring for Java projects.
- [ ] Do not assume internal library behavior.
- [ ] Do not assume cloud provider or vendor platform.
- [ ] Do not assume command availability.
- [ ] Label assumptions explicitly.

## Output Readiness

- [ ] Backend task classification included.
- [ ] Primary scope included.
- [ ] Secondary scopes included.
- [ ] Risks included.
- [ ] Context needed included.
- [ ] Recommended Skill included.
- [ ] Suggested next action included.
- [ ] Handoff prompt included when useful.
