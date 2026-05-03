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

## Required Inputs

| Input | Required? | Notes |
|-------|-----------|-------|
| Feature requirements or user story | Required | Minimum viable description of intended behavior |
| Current system behavior | Recommended | What exists today that this changes or extends |
| Existing API/schema contracts | If affected | Required when changing public APIs or persistence |
| Security and access control constraints | If known | Auth model, tenant scope, data sensitivity |
| Scale/performance constraints | If known | Expected load, latency SLAs, data volume |
| Repo context (modules, frameworks) | If available | Avoids inventing internal library behavior |

## Non-Goals

Do not:

- Implement code directly.
- Estimate timeline or effort.
- Assume Spring, FastAPI, NestJS, cloud provider, database, queue, or vendor-specific platform.
- Invent internal library APIs or framework behavior.
- Skip security, validation, observability, or testing for production-impacting work.
- Produce a large speculative design when requirements are insufficient.

## Safety Boundaries

- Do not implement code — output is design only; hand off to `backend-feature-implementation` for execution.
- Do not produce a speculative design when requirements are insufficient — clarify feature intent first.
- Do not invent internal library APIs, framework behavior, file paths, or validation commands.
- Flag open questions explicitly rather than silently resolving ambiguous security, data, or compatibility concerns.
- Require human approval before design decisions that affect public APIs, schema migrations, security model, or production configuration.

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

1. **Understand and model** — clarify feature intent, domain concepts, actors, and state transitions.
2. **Design contracts** — define API/interface impact, application workflow, data impact, and security/trust boundaries.
3. **Design operations** — identify integration boundaries, reliability/performance/observability concerns, and validation strategy.
4. **Record and hand off** — document assumptions, open questions, risks, and produce handoff to `backend-feature-implementation`.

See `references/backend-design-workflow.md` for detailed steps and quality bar per phase.

## Evidence Rules

- Distinguish facts, assumptions, and hypotheses.
- If repository context is missing, say what must be inspected before implementation.
- If internal libraries are involved, infer behavior from actual usage and tests only.
- If validation commands are unknown, do not invent them.

## Expected Outputs

Output type: `mixed` — spec (API contract, domain model), plan (workflow steps, implementation handoff), recommendation (design options with trade-offs), risk register (risks and open questions), summary (design overview).

Primary template: `templates/backend-feature-design-doc.md`
Quick design: `templates/backend-technical-design-summary.md`
Option analysis: `templates/backend-design-options.md`
API and data flow: `templates/backend-api-data-flow.md`
Risk tracking: `templates/backend-risk-and-validation-plan.md`
