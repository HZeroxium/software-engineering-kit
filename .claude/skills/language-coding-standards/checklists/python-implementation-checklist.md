# Python Implementation Checklist

## Context

- [ ] Python version is known or uncertainty is stated.
- [ ] Existing project style is inspected.
- [ ] Existing typing, linting, and test conventions are inspected.
- [ ] Public API impact is understood.

## Types and Models

- [ ] Public functions have useful type hints.
- [ ] `Any` is avoided unless justified.
- [ ] `None` handling is explicit.
- [ ] Dataclass/Pydantic usage follows project convention.
- [ ] External input is validated at boundaries.

## Correctness

- [ ] Errors are specific.
- [ ] Exceptions are not swallowed.
- [ ] Boundary errors are translated safely.
- [ ] Mutable defaults are avoided.
- [ ] Time/random/external dependencies are controllable when tested.

## Async and I/O

- [ ] Blocking calls are not used inside async code.
- [ ] Async calls are awaited.
- [ ] Timeouts are considered.
- [ ] Retries are bounded and idempotent.
- [ ] Background tasks have lifecycle/error handling.

## Observability and Tests

- [ ] Logs are useful and safe.
- [ ] Tests cover success, failure, and edge cases.
- [ ] Validation commands are discovered from repo.
