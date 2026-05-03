---
purpose: SOLID principles and useful backend design patterns — vocabulary for architecture and code structure decisions
load-when: Reviewing code structure, responsibility allocation, or pattern selection
tier: foundational
see-also:
  - application-services.md
---

# SOLID and Design Patterns

## Purpose

Use design principles to reduce risk, not to add ceremony.

## Practical SOLID Use

- Single Responsibility: one reason to change.
- Open/Closed: extend stable variation points.
- Liskov: implementations preserve contract expectations.
- Interface Segregation: callers depend on what they use.
- Dependency Inversion: core policy does not depend on infrastructure detail.

## Useful Backend Patterns

- Strategy for replaceable policies.
- Factory for complex object creation.
- Repository for persistence abstraction where useful.
- Adapter for external systems.
- Command handler/use case for operations.
- Specification or policy object for complex rules.
- State machine for lifecycle.

## Smells

- Pattern used without real variation.
- Large inheritance hierarchy.
- Interface for every class.
- God service with many unrelated dependencies.
- Domain logic hidden in factories or mappers.

## SOLID in Backend Practice

### Single Responsibility

A class has one reason to change. In backend services, this means:

- An application service orchestrates one use case — it does not own unrelated workflows.
- A domain entity manages its own invariants — it does not perform persistence.
- A repository abstracts data access — it does not enforce business rules.

Violation signal: a class changes when the use case logic changes AND when the data format changes AND when the notification strategy changes.

### Open/Closed

Extend behavior without modifying stable code. Useful when:

- A new payment method, notification channel, or export format must be added.
- The core orchestration should not change as variants grow.

Apply via Strategy or Adapter at real variation points. Do not pre-abstract every class speculatively.

### Liskov Substitution

A subtype must behave consistently with its contract. In backend code:

- A read-only repository must not silently drop writes — it should throw, not no-op.
- A decorator must preserve the original behavior except where it explicitly extends it.
- A mock in tests must honor the same invariants as the real implementation.

### Interface Segregation

Callers depend only on what they use. Apply when:

- A component needs read access but is forced to accept a write-capable dependency.
- A use case only queries data but receives a full repository interface with mutation methods.
- A notification service only needs `send()` but receives a full messaging client.

Do not split every interface without a real consumer mismatch.

### Dependency Inversion

Core business logic depends on abstractions, not infrastructure implementations. In practice:

- Use-case classes depend on repository interfaces, not JPA repositories or SQL code.
- Domain logic depends on clock abstractions, not `System.currentTimeMillis()` directly.
- Adapters implement ports; ports are owned by the application or domain layer.

This is the most important principle for testability and infrastructure independence.

## Pattern Selection Guide

| Problem | Pattern | Avoid when |
| ------- | ------- | ---------- |
| Replaceable algorithm or policy | Strategy | Only one implementation exists now and none is planned |
| Complex object construction with variants | Factory / Builder | Construction is simple enough for a constructor |
| Persistence abstraction | Repository | ORM queries are spread across services anyway |
| External system isolation | Adapter | The external system is trivial and unlikely to change |
| Operation dispatch | Command handler / Use case | A simple function call already separates concerns |
| Complex conditional business rules | Specification / Policy object | Conditions are simple enough inline |
| Entity lifecycle with transition rules | State machine | Entity has only one or two valid states |

## Review Questions

- Does this abstraction hide a real variation point, or just add indirection?
- If I remove this interface, does the core logic still compile without infrastructure details?
- Does this class change for more than one reason today?
- Can this use case be tested without instantiating any infrastructure class?
