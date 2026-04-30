# Python Coding Standards

## Core Principle

Prefer clear, typed, testable Python with explicit boundaries and predictable runtime behavior.

## Type Hints

- Add type hints for public functions, service functions, and complex internal functions.
- Avoid `Any` unless boundary or dynamic behavior justifies it.
- Use precise collection types.
- Use `Optional` / `| None` only when `None` is valid.
- Keep return types explicit for non-trivial functions.
- Do not pretend type hints validate runtime input.

## Data Models

Use dataclasses when:

- Representing internal value objects.
- Storing structured data with simple behavior.
- Immutability or equality is useful.

Use Pydantic or project-standard validation models when:

- Parsing external input.
- Validating API payloads.
- Producing structured external output.

Do not introduce Pydantic or other libraries unless already present or user-approved.

## Error Handling

- Raise specific exceptions.
- Preserve cause with exception chaining when useful.
- Do not swallow exceptions silently.
- Convert infrastructure errors at boundaries.
- Avoid broad `except Exception` unless adding context, cleanup, retry classification, or boundary translation.
- Avoid exposing sensitive details in errors.

## Async Correctness

- Do not use blocking I/O inside async code.
- Await async calls.
- Bound concurrency.
- Use timeouts for external calls.
- Avoid fire-and-forget tasks unless lifecycle and error handling are clear.
- Handle cancellation where relevant.
- Avoid shared mutable state across concurrent tasks.

## API Timeouts and Retries

- Use explicit timeouts for external API calls.
- Retry only retryable errors.
- Bound retries.
- Use backoff and jitter when appropriate.
- Ensure retried operations are idempotent.
- Log failures safely.

## Dependency Boundaries

- Keep external service clients behind small boundary functions/classes.
- Keep business logic separate from transport/framework code.
- Avoid global clients unless project convention supports it.
- Inject dependencies for testability where useful.

## Logging

- Use structured logging if project supports it.
- Log safe identifiers.
- Avoid logging secrets, tokens, credentials, customer data, or full sensitive payloads.
- Avoid noisy logs inside tight loops.

## Testability

- Keep pure logic separate from I/O.
- Control time, randomness, and external dependencies.
- Use fixtures for repeated setup.
- Add regression tests for bug fixes.
- Avoid tests that depend on network or local machine state.
