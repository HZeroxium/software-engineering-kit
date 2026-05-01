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
