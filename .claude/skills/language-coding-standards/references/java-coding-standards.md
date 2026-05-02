---
purpose: Java language-level coding standards for type-safe, maintainable, production-grade implementation and review
load-when: Working in Java code or reviewing Java-specific language, structure, runtime, or maintainability choices
tier: domain
see-also:
  - error-handling-standards.md
  - dependency-and-library-usage.md
  - naming-and-readability.md
  - immutability-and-state.md
  - concurrency-and-async.md
---

# Java Coding Standards

## Core Principle

Prefer clear, boring, type-safe Java that matches the project’s Java version and existing conventions.

Do not use language features unavailable in the project’s configured Java version.

## Class and Interface Design

- Keep classes cohesive.
- Prefer composition over inheritance unless inheritance models a real subtype relationship.
- Use interfaces for meaningful boundaries, not ceremony.
- Avoid one-method interfaces unless they represent a real port, strategy, callback, or test seam.
- Keep constructors valid and explicit.
- Avoid partially initialized objects.
- Keep public APIs small and intentional.

## Immutability

Prefer immutability for:

- Value objects.
- DTOs.
- Configuration objects.
- Domain events.
- Command/query objects.

Use mutable state only when lifecycle and ownership are clear.

## Null Handling

- Avoid returning `null` for collections; prefer empty collections.
- Validate required inputs at boundaries.
- Use `Optional` for return values when absence is expected and project style allows it.
- Avoid `Optional` for fields and method parameters unless project convention allows it.
- Do not hide nullability assumptions.

## Exceptions and Error Mapping

- Use exceptions for exceptional conditions, not normal control flow.
- Preserve cause when wrapping exceptions.
- Map internal exceptions to API errors at boundaries.
- Avoid leaking internal details to clients.
- Keep domain errors distinguishable from infrastructure errors.
- Do not catch broad exceptions unless adding useful handling or context.

## Collections and Stream API

- Use streams when they improve clarity.
- Use loops when they are clearer or easier to debug.
- Avoid side effects inside streams.
- Avoid complex nested stream chains.
- Avoid repeated collection scans for large data.
- Use appropriate collection types for lookup, ordering, uniqueness, and concurrency.

## Generics

- Use generics to improve type safety.
- Avoid raw types.
- Avoid over-generic APIs that obscure domain meaning.
- Use bounded wildcards when needed, but prefer readability.

## Concurrency and Thread Safety

- Make shared mutable state explicit.
- Prefer immutable data and local variables.
- Use thread-safe collections only when they match the access pattern.
- Avoid blocking calls on event-loop/reactive threads.
- Bound thread pools and queues.
- Make retries idempotent.
- Close resources deterministically.

## Resource Lifecycle

- Use try-with-resources for closeable resources.
- Avoid leaking streams, files, sockets, clients, or database resources.
- Avoid creating expensive clients repeatedly if the project expects shared clients.
- Respect framework lifecycle conventions.

## DTO / Domain / Entity Boundaries

- Do not mix external API DTOs, domain objects, and persistence entities accidentally.
- Map at boundaries when behavior or compatibility requires it.
- Avoid exposing persistence entities as public API unless the project intentionally does so.
- Keep validation close to the boundary where invalid input enters.

## Dependency Injection Boundaries

- Use DI according to project style.
- Prefer constructor injection where supported.
- Avoid service locator patterns unless project convention requires it.
- Keep infrastructure dependencies out of domain logic when possible.
- Do not create abstractions only for mocking if a simpler test strategy is better.

## Logging and Observability

- Log useful events and failures.
- Include safe identifiers.
- Do not log secrets or sensitive payloads.
- Avoid noisy logs in hot paths.
- Use metrics/traces when behavior or failure modes affect production operations.
- Avoid high-cardinality metric labels.

## Testability

- Keep business logic testable without full framework boot when practical.
- Inject time/random/external clients when behavior depends on them.
- Avoid static/global state.
- Add regression tests for bug fixes.
