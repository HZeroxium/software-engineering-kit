---
name: backend-application-architecture
description: Framework-agnostic backend Skill for application services, use-case orchestration, transaction boundaries, workflows, state machines, module boundaries, dependency architecture, Clean/Hexagonal/Layered architecture, SOLID, and design patterns.
---

# Backend Application Architecture

Use this Skill when designing or reviewing backend application service logic, use-case orchestration, module boundaries, dependency direction, transaction boundaries, workflows, state machines, or architectural refactors.

## Purpose

Analyze and design backend application architecture and use-case orchestration.

This Skill covers:

- Application services.
- Command/query separation.
- Transaction boundaries.
- Workflow orchestration.
- State machines.
- Dependency architecture.
- Module boundaries.
- Composition root.
- Ports and adapters.
- Clean, Hexagonal, and Layered architecture.
- SOLID and design patterns.

## Activation Criteria

Use when:

- Backend code risks becoming a god service.
- Application logic is tightly coupled to infrastructure.
- Transaction boundaries are unclear.
- Workflow/state transition logic is scattered.
- Modules have unclear ownership.
- A refactor affects dependency direction or architecture.
- The user asks where logic should live.

## Non-Goals

Do not:

- Assume Spring, dependency injection frameworks, ORM behavior, or internal platform libraries.
- Redesign the whole codebase unless explicitly requested.
- Add abstractions without a real variation point.
- Move logic only for pattern purity.
- Implement code before architecture risk is understood.

## Workflow

1. Identify use case, actor, command/query, and expected outcome.
2. Summarize current architecture if context exists.
3. Identify orchestration steps and side effects.
4. Analyze transaction boundaries and consistency.
5. Analyze state/workflow model.
6. Review module boundaries and dependency direction.
7. Identify over-coupling, god services, anemic models, and infrastructure leakage.
8. Recommend architecture option with trade-offs.
9. Define validation strategy.
10. Separate confirmed facts, assumptions, and unknowns.

## Expected Output

Return:

- Current architecture summary if context exists.
- Use-case orchestration model.
- Module boundary analysis.
- Dependency direction review.
- Transaction boundary analysis.
- State/workflow model.
- Recommended architecture option and trade-offs.
- Validation strategy.

## Safety Boundaries

Ask for clarification or repo evidence when:

- Transaction semantics depend on framework behavior.
- Internal libraries control lifecycle, dependency injection, transactions, or messaging.
- Refactor scope is broad.
- Public contracts, migrations, security, or production config may be affected.
