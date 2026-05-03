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

## Required Inputs

- Use-case description or problem statement.
- Existing code context when available (service classes, module structure, config files).
- Current architecture description or relevant file paths.
- Internal library or framework constraints if they affect transaction, DI, or lifecycle.
- Refactor scope and compatibility requirements if applicable.

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

## Expected Outputs

**Output type:** `mixed`

| Component | Type |
| --------- | ---- |
| Current architecture summary | analysis |
| Use-case orchestration model | plan |
| Module boundary analysis | analysis |
| Dependency direction review | analysis |
| Transaction boundary analysis | analysis |
| State/workflow model | spec |
| Recommended architecture option and trade-offs | recommendation |
| Validation strategy | checklist |

Omit components that are not relevant to the task. Always include Recommended architecture option.

## Supporting Files

Load on demand — do not load all at once. See `references/reference-index.md` for the full graph.

| File | Tier | Load when |
| ---- | ---- | --------- |
| `references/clean-hexagonal-layered-architecture.md` | foundational | Architecture style selection or layer responsibility review |
| `references/dependency-architecture.md` | foundational | Dependency direction, cycles, or coupling review |
| `references/solid-and-design-patterns.md` | foundational | Code structure, responsibility, or pattern selection |
| `references/application-services.md` | domain | Designing or reviewing application service boundaries |
| `references/use-case-orchestration.md` | domain | Designing or reviewing use-case orchestration logic |
| `references/transaction-boundaries.md` | domain | Transaction boundaries, atomicity, or side effect ordering |
| `references/modular-monolith-and-multi-module.md` | domain | Module boundaries, ownership, or dependency cycles |
| `references/workflow-orchestration.md` | domain | Multi-step async/event-driven/job workflow design |
| `references/state-machines.md` | domain | Entity with meaningful lifecycle and transition rules |
| `references/java-application-architecture-examples.md` | scenario | Java code examples explicitly requested |
| `checklists/application-architecture-checklist.md` | — | Final architecture review pass |
| `checklists/module-boundary-checklist.md` | — | Module boundary analysis |
| `checklists/transaction-boundary-checklist.md` | — | Transaction boundary analysis |
| `templates/application-architecture-review.md` | — | Producing a structured architecture review output |
| `templates/use-case-orchestration-plan.md` | — | Producing an orchestration plan output |
| `templates/transaction-boundary-analysis.md` | — | Producing a transaction boundary analysis output |
| `templates/module-boundary-review.md` | — | Producing a module boundary review output |
| `templates/state-machine-design.md` | — | Producing a state machine design output |
| `examples/java-use-case-orchestration-example.md` | — | Java orchestration worked example |

## Safety Boundaries

Ask for clarification or repo evidence when:

- Transaction semantics depend on framework behavior.
- Internal libraries control lifecycle, dependency injection, transactions, or messaging.
- Refactor scope is broad.
- Public contracts, migrations, security, or production config may be affected.

## Failure Handling

If required inputs are missing:

- Ask for the use-case description and existing code context before proceeding.
- Do not assume framework behavior (transactions, DI, lifecycle) without repo evidence.
- Limit scope to what can be confirmed; mark unknowns explicitly.

If scope is too broad (e.g., "redesign the whole codebase"):

- Narrow to one module or use case.
- Return findings and a prioritized recommendation rather than a full redesign.

If architecture depends on internal platform libraries with unknown behavior:

- State the assumption explicitly.
- Recommend the user confirm behavior from repo docs or code before acting on the recommendation.
