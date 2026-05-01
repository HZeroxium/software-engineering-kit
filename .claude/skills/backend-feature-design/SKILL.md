---
name: backend-feature-design
description: Framework-agnostic backend feature design workflow. Use to translate backend requirements into capability design, API/interface impact, application workflow, data changes, security/trust model, integration needs, reliability/performance/observability concerns, validation strategy, and implementation handoff.
---

# Backend Feature Design

Use this Skill when the user asks to design a backend feature, API, service/module behavior, workflow, data flow, state transition, integration, or backend architecture.

This Skill creates backend technical design. It does not estimate work. Use `requirements-analysis-and-estimation` for estimation.

## Purpose

Translate feature intent or requirements into a backend design that is safe to implement.

The design should cover:

- Problem framing.
- Backend capability and domain concepts.
- API/interface impact.
- Application workflow and use-case orchestration.
- Data/persistence impact.
- Security/trust assumptions.
- Integration and distributed communication impact.
- Reliability, performance, and observability concerns.
- Test and validation strategy.
- Risks and open questions.
- Handoff to `backend-feature-implementation`.

## Activation Criteria

Use when:

- Requirements are known enough for technical design.
- The user asks to design a backend feature, API, service behavior, data flow, state transition, integration, or workflow.
- The task is non-trivial and should be designed before implementation.
- The work may affect backend APIs, business logic, persistence, security, integrations, reliability, performance, observability, or tests.

## Non-Goals

Do not:

- Implement code directly.
- Estimate timeline or effort.
- Assume Spring, FastAPI, NestJS, cloud provider, database, queue, or vendor-specific platform.
- Invent internal library APIs or framework behavior.
- Skip security, validation, observability, or testing for production-impacting work.
- Produce a large speculative design when requirements are insufficient.

## Default Backend Scopes

Analyze across these scopes as relevant:

1. Domain/API.
2. Application architecture.
3. Data/persistence.
4. Security/trust.
5. Integration/distributed communication.
6. Reliability/resilience.
7. Performance/scalability.
8. Observability/operations.
9. AI/governance/quality.

## Workflow

1. Clarify the feature intent and business capability.
2. Identify domain concepts, invariants, actors, and state transitions.
3. Define API/interface impact without leaking implementation details.
4. Design application workflow and orchestration.
5. Identify data ownership, persistence changes, consistency, caching, and migration impact.
6. Identify security/trust boundaries, authorization, tenant isolation, secrets, and audit needs.
7. Identify sync/async integration boundaries, retries, timeouts, idempotency, and failure handling.
8. Identify reliability, performance, scalability, observability, and operational concerns.
9. Define test and validation strategy.
10. Record assumptions, open questions, trade-offs, and risks.
11. Produce handoff to `backend-feature-implementation`.

## Evidence Rules

- Distinguish facts, assumptions, and hypotheses.
- If repository context is missing, say what must be inspected before implementation.
- If internal libraries are involved, infer behavior from actual usage and tests only.
- If validation commands are unknown, do not invent them.

## Expected Output

Use the templates when useful:

- `templates/backend-feature-design-doc.md`
- `templates/backend-technical-design-summary.md`
- `templates/backend-design-options.md`
- `templates/backend-api-data-flow.md`
- `templates/backend-risk-and-validation-plan.md`

## Final Response Shape

```text
# Backend Feature Design

## Summary
...

## Problem Framing
...

## Backend Capability and Domain Concepts
...

## API / Interface Impact
...

## Application Workflow
...

## Data / Persistence Impact
...

## Security and Trust
...

## Integration and Distributed Communication
...

## Reliability, Performance, and Observability
...

## Test and Validation Strategy
...

## Risks and Open Questions
...

## Handoff to backend-feature-implementation
...
```
