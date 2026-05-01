# Dependency Architecture

## Purpose

Keep backend code understandable, testable, and resilient to change.

## Concepts

- Dependency direction.
- Dependency inversion.
- Dependency injection.
- Composition root.
- Ports and adapters.
- Module boundaries.

## Review Questions

- Does core logic depend on infrastructure?
- Are dependencies explicit?
- Are there cycles?
- Are abstractions meaningful?
- Can code be tested without external systems?
- Where are dependencies assembled?

## Smells

- Static global accessors.
- Hidden service locators.
- Common module dumping ground.
- Infrastructure imports in domain logic.
- Cyclic module dependencies.
- New abstraction with only one speculative implementation.
