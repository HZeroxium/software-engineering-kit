# Hexagonal Architecture

## Intent

Separate application core from external actors through ports and adapters.

The application defines what it needs. Adapters implement how external systems are used.

## Key Concepts

- Inbound ports: use cases exposed to callers.
- Outbound ports: capabilities the application needs from outside.
- Inbound adapters: REST controllers, message consumers, CLI.
- Outbound adapters: database repositories, HTTP clients, queues, file systems.
- Application core: business logic and orchestration.

## Good Fit

Use when:

- External systems change often.
- Multiple adapters use the same use case.
- Business logic must be tested without real infrastructure.
- Integration boundaries are important.
- You need clear separation between domain and infrastructure.

## Risks

- Too many ports for trivial code.
- One-interface-per-class without value.
- Mock-heavy tests that miss integration problems.
- Boundary naming becomes inconsistent.
- Adapters leak infrastructure exceptions into domain.

## Review Questions

- Are ports named in business terms?
- Does the core depend on abstractions it owns?
- Are adapters thin and replaceable?
- Are infrastructure exceptions translated at boundaries?
- Are external data models mapped before entering the core?
- Are tests split between core unit tests and adapter integration tests?
