---
name: backend-domain-and-api-design
description: Framework-agnostic backend Skill for domain modeling, business logic correctness, API/interface design, error models, versioning, pagination, filtering, sorting, idempotency, retry safety, and compatibility.
---

# Backend Domain and API Design

## Purpose

Analyze and design backend domain capabilities and API/interface contracts.

This Skill owns:

- Domain modeling.
- Bounded contexts and business capabilities.
- Business invariants.
- State transitions.
- Domain events.
- API style selection.
- API contracts.
- Error models.
- Versioning and compatibility.
- Pagination, filtering, and sorting.
- Idempotency and retry safety.
- Business logic correctness.

## Activation Criteria

Use when:

- Designing a new backend domain model or business capability.
- Reviewing existing domain model for correctness, invariants, or state transitions.
- Designing or reviewing API/interface contracts (REST-like, RPC, event, internal module).
- Analyzing breaking changes or backward compatibility requirements.
- Designing or reviewing error model semantics.
- Analyzing idempotency or retry safety for operations with side effects.
- Designing pagination, filtering, or sorting for list APIs.
- Reviewing business logic correctness or missing invariants.
- Identifying bounded context or capability ownership issues.

## Non-Goals

Do not:

- Assume Spring Boot, Spring MVC, JPA, Hibernate, FastAPI, NestJS, Kafka, Kubernetes, or any specific technology.
- Invent internal framework or library behavior.
- Implement code directly unless the user explicitly asks for implementation after design.
- Treat API design as only CRUD over database tables.
- Ignore business invariants, compatibility, or error semantics.

## Required Inputs

- Business capability description or use-case statement.
- Existing API schema, contract, or interface definition when reviewing.
- Current domain model or entity descriptions when extending or reviewing.
- Known clients or consumer context.
- Compatibility constraints (breaking changes allowed or not).
- Internal framework or convention constraints affecting domain behavior, if relevant.
- Idempotency and retry requirements when the operation has side effects.

## Workflow

1. Identify the backend capability and business intent.
2. Extract domain concepts, actors, invariants, and valid state transitions.
3. Identify business rules and correctness risks.
4. Select API/interface style based on caller needs and workflow semantics.
5. Define contract shape, validation boundaries, errors, and compatibility.
6. Analyze idempotency and retry safety.
7. Review pagination, filtering, sorting, and versioning where relevant.
8. Define test cases and validation strategy.
9. Separate confirmed facts, assumptions, hypotheses, and open questions.

## Expected Outputs

**Output type:** `mixed`

| Component | Type |
| --------- | ---- |
| Domain model summary | analysis |
| Business rules and invariants | spec |
| State transition model | spec |
| API/interface design or review | spec |
| Error model | spec |
| Idempotency and retry-safety analysis | analysis |
| Compatibility and versioning assessment | analysis |
| Pagination/filtering/sorting design | spec |
| Test cases and validation strategy | checklist |
| Risks and open questions | analysis |

Omit components not relevant to the task. Always include domain model summary and risks.

## Supporting Files

Load on demand — do not load all at once. See `references/reference-index.md` for the full graph.

| File | Tier | Load when |
| ---- | ---- | --------- |
| `references/domain-modeling.md` | foundational | Domain modeling, entity/value object/aggregate design needed |
| `references/bounded-contexts-and-business-capabilities.md` | foundational | Bounded context, capability ownership, or model language review |
| `references/business-invariants-and-state-transitions.md` | foundational | Invariants, state transitions, or business correctness review |
| `references/api-style-selection.md` | domain | Comparing or selecting API/interface styles |
| `references/api-contracts-versioning-and-compatibility.md` | domain | API contract review, versioning, or compatibility analysis |
| `references/error-models.md` | domain | Error model design or review |
| `references/idempotency-and-retry-safety.md` | domain | Idempotency, retry safety, or at-least-once delivery analysis |
| `references/pagination-filtering-sorting.md` | domain | List API pagination, filtering, or sorting design |
| `references/java-domain-modeling-examples.md` | scenario | Java code examples explicitly requested |
| `checklists/domain-design-checklist.md` | — | Final domain model review pass |
| `checklists/api-design-checklist.md` | — | Final API design review pass |
| `checklists/business-logic-correctness-checklist.md` | — | Business logic correctness review |
| `templates/domain-and-api-design-report.md` | — | Producing a full domain and API design report |
| `templates/api-contract-review.md` | — | Producing an API contract review output |
| `templates/business-logic-correctness-review.md` | — | Producing a business logic correctness review |
| `templates/error-model-design.md` | — | Producing an error model design |
| `templates/idempotency-analysis.md` | — | Producing an idempotency analysis |
| `examples/java-domain-api-design-example.md` | — | Java worked example |

## Safety Boundaries

Ask for clarification or repository evidence when:

- Business rules are ambiguous.
- Public API compatibility is unclear.
- Authorization or tenant ownership affects the domain behavior.
- Idempotency semantics affect money, orders, jobs, notifications, or external side effects.
- Internal libraries or framework conventions are required to understand behavior.

Require human approval before proposing breaking public contract changes.

## Failure Handling

If required inputs are missing:

- Ask for the business capability description and use case before proceeding.
- Do not assume business rules, invariants, or API contracts without evidence from code, tests, or user-provided context.
- Limit scope to what can be confirmed; mark unknowns explicitly.

If scope is too broad (e.g., "redesign the entire domain model"):

- Narrow to one bounded context or one use case.
- Return findings and prioritized recommendations rather than a full redesign.

If public API compatibility is unclear:

- Default to assuming backward compatibility is required.
- Flag any proposed change as potentially breaking and require human review before finalizing.

If idempotency semantics involve money, orders, jobs, notifications, or external system side effects:

- State explicitly that human review is required before implementation.
