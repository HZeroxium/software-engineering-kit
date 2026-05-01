---
name: backend-domain-and-api-design
description: Framework-agnostic backend Skill for domain modeling, business logic correctness, API/interface design, error models, versioning, pagination, filtering, sorting, idempotency, retry safety, and compatibility.
---

# Backend Domain and API Design

Use this Skill when the task involves domain modeling, business rules, API/interface design, API review, business logic correctness, state transitions, API contract changes, error model design, idempotency, retry safety, or compatibility.

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

## Non-Goals

Do not:

- Assume Spring Boot, Spring MVC, JPA, Hibernate, FastAPI, NestJS, Kafka, Kubernetes, or any specific technology.
- Invent internal framework or library behavior.
- Implement code directly unless the user explicitly asks for implementation after design.
- Treat API design as only CRUD over database tables.
- Ignore business invariants, compatibility, or error semantics.

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

## Expected Output

Return:

- Domain model summary.
- Business rules and invariants.
- Valid and invalid state transitions.
- API/interface design or review.
- Error model.
- Idempotency and retry-safety analysis.
- Compatibility and versioning considerations.
- Test cases and validation strategy.
- Risks and open questions.

Use templates in `templates/` and references in `references/` when deeper structure is needed.

## Safety Boundaries

Ask for clarification or repository evidence when:

- Business rules are ambiguous.
- Public API compatibility is unclear.
- Authorization or tenant ownership affects the domain behavior.
- Idempotency semantics affect money, orders, jobs, notifications, or external side effects.
- Internal libraries or framework conventions are required to understand behavior.

Require human approval before proposing breaking public contract changes.
