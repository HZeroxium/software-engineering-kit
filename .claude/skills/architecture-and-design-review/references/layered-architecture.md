# Layered Architecture

## Intent

Organize code into layers with clear responsibilities and controlled dependency direction.

Common backend layers:

- Controller/API layer.
- Application/service layer.
- Domain/business layer.
- Persistence/repository layer.
- Infrastructure/integration layer.

## Good Fit

Use when:

- Application is mostly request/response.
- Team prefers conventional structure.
- Framework conventions are strong.
- Simple module boundaries are enough.
- Maintainability is improved by predictable layering.

## Risks

- Anemic service layer that only forwards calls.
- Fat controllers.
- Domain logic scattered across layers.
- Persistence entities leaking to API.
- Circular dependencies.
- Too many layers for simple features.
- Cross-layer shortcuts that become permanent.

## Review Questions

- Does each layer have a clear responsibility?
- Are dependencies flowing in the expected direction?
- Are controllers thin?
- Is business logic in the appropriate layer?
- Are repositories focused on persistence concerns?
- Are transaction boundaries clear?
- Are DTO/domain/entity mappings intentional?
- Are exceptions mapped at the correct boundary?

## Minimal Design Rule

Do not add layers just for appearance.

Add a layer or abstraction when it improves:

- Correctness.
- Testability.
- Separation of concerns.
- Change isolation.
- Dependency control.
- Team comprehension.
