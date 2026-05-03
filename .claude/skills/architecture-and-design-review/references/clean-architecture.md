---
purpose: Dependency inversion and layer isolation; separating business rules from frameworks, databases, and UI
load-when: Design separates business logic from infrastructure; dependency direction or testability is a concern
tier: domain
see-also:
  - hexagonal-architecture.md
---

# Clean Architecture

## Intent

Separate business rules from frameworks, databases, UI, and external systems.

Use this reference when a design needs stronger dependency direction, testability, and domain isolation.

## Core Rule

Dependencies should point inward toward stable business rules.

Outer layers know inner layers. Inner layers should not depend on outer frameworks, databases, HTTP clients, queues, or UI details.

## Typical Boundaries

- Domain model: business concepts, invariants, state transitions.
- Use cases/application services: orchestration of business operations.
- Interface adapters: controllers, presenters, gateways, repositories.
- Frameworks/infrastructure: web framework, database, message broker, external APIs.

## Good Fit

Use when:

- Business logic is complex.
- Testability matters.
- Framework churn is expected.
- Domain rules should survive infrastructure changes.
- Multiple delivery mechanisms exist, such as REST, messaging, CLI, or jobs.

## Poor Fit

Avoid over-applying when:

- CRUD is simple.
- Domain logic is minimal.
- Indirection cost exceeds benefit.
- Team conventions are strongly framework-oriented.
- The codebase is small and stable.

## Review Questions

- Are domain rules independent of framework details?
- Are use cases explicit?
- Are infrastructure dependencies behind ports/interfaces when useful?
- Are DTOs, entities, and domain objects mixed accidentally?
- Can business rules be tested without booting the full framework?
- Does dependency direction follow the intended boundary?
- Is the architecture simpler than the problem requires, or more complex?

## Java Backend Notes

- Keep transaction boundaries in application/service layer or framework boundary according to repo convention.
- Avoid placing domain rules only in controllers.
- Avoid leaking persistence entities into external API contracts unless the project intentionally does so.
- Use interfaces only when they create useful boundary or testability value.
- Do not create unnecessary abstractions for one implementation unless evolution or testing justifies it.
