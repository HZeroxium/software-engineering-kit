---
purpose: SOLID heuristics for evaluating module and class responsibility, coupling, and abstraction quality
load-when: Reviewing class or module design for cohesion, coupling, responsibility scope, or abstraction quality
tier: foundational
see-also:
  - design-patterns.md
  - clean-architecture.md
---

# SOLID Principles

## Purpose

Use SOLID as design heuristics, not rigid rules.

## Single Responsibility Principle

A module/class/function should have one clear reason to change.

Review:

- Is responsibility cohesive?
- Is business logic mixed with infrastructure?
- Is validation mixed with persistence or presentation?
- Would unrelated changes affect this class?

## Open/Closed Principle

Code should be extensible without risky modification when variation is expected.

Review:

- Is extension actually needed?
- Would abstraction reduce or increase complexity?
- Is a simple conditional better for current scope?

## Liskov Substitution Principle

Subtypes should preserve expected behavior of their base types.

Review:

- Do subclasses violate base contracts?
- Are unsupported operations thrown unexpectedly?
- Are invariants weakened?

## Interface Segregation Principle

Clients should not depend on methods they do not use.

Review:

- Are interfaces too broad?
- Are dependencies forced to implement unused methods?
- Would smaller ports improve clarity?

## Dependency Inversion Principle

High-level policy should not depend directly on low-level details when that creates coupling.

Review:

- Does domain/application logic depend on infrastructure?
- Is the abstraction owned by the core or by the infrastructure?
- Is dependency injection used for meaningful boundaries, not ceremony?

## Anti-Pattern

Do not use SOLID to justify unnecessary abstractions, factories, or interfaces.
