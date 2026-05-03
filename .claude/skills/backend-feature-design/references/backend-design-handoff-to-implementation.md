---
purpose: Checklist of handoff requirements and a ready-to-use prompt template for handing design to backend-feature-implementation
load-when: Design is complete and ready to hand off to backend-feature-implementation
tier: scenario
see-also: []
---

# Backend Design Handoff to Implementation

## Purpose

Use this reference to turn a backend design into a safe implementation task.

## Handoff Must Include

- Feature summary.
- Primary behavior.
- Affected backend scopes.
- Expected module/file areas if known.
- API/interface contract.
- Workflow steps.
- Data changes.
- Security/trust requirements.
- Integration behavior.
- Failure handling.
- Observability requirements.
- Test strategy.
- Validation commands if known.
- Risks and approval gates.
- Open questions.

## Handoff Prompt Template

```text
Use backend-feature-implementation.

Task:
<implement this backend feature>

Design summary:
<summary>

Behavior:
<expected behavior>

API/interface:
<contract>

Workflow:
<steps>

Data changes:
<data impact>

Security/trust requirements:
<auth/authz/tenant/secrets/audit>

Integration requirements:
<sync/async/retry/timeout/idempotency>

Observability requirements:
<metrics/logs/traces/alerts>

Validation:
<tests/checks/commands>

Constraints:
- Use repository conventions.
- Do not assume a framework.
- Do not invent internal library behavior.
- Keep changes small and reviewable.
- Ask before high-risk changes.
```
