# Clean, Hexagonal, and Layered Architecture

## Purpose

Use architecture styles pragmatically. Do not force patterns without a real problem.

## Layered Architecture

```text
API / Transport
Application / Use Case
Domain / Business
Infrastructure / Adapter
```

## Hexagonal / Ports and Adapters

Core logic depends on ports. Infrastructure implements adapters.

## Clean Architecture

Inner policies should not depend on outer infrastructure details.

## Use These Patterns When

- Domain logic needs testability.
- Infrastructure choices may change.
- Multiple adapters exist.
- Business rules are complex.
- External systems should be isolated.

## Avoid

- Pattern purity that increases complexity.
- Interfaces for every class without reason.
- Moving code without improving boundaries.
- Assuming framework annotations define architecture.
