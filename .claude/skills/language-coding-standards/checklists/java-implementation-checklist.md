# Java Implementation Checklist

## Context

- [ ] Java version is known or uncertainty is stated.
- [ ] Existing project style is inspected.
- [ ] Framework conventions are respected.
- [ ] Public API impact is understood.

## Design

- [ ] Class has cohesive responsibility.
- [ ] Interface exists only when useful.
- [ ] Dependency direction is intentional.
- [ ] DTO/domain/entity boundaries are clear.
- [ ] DI boundary follows project convention.

## Correctness

- [ ] Required inputs are validated.
- [ ] Null handling is explicit.
- [ ] Collections are not unexpectedly null.
- [ ] State transitions are valid.
- [ ] Invariants are protected.
- [ ] Exceptions are mapped at boundaries.

## Concurrency and Resources

- [ ] Shared mutable state is safe.
- [ ] Blocking calls are not in unsafe paths.
- [ ] Timeouts/retries are considered.
- [ ] Resources are closed.
- [ ] Transaction boundaries are clear.

## Observability and Tests

- [ ] Logs are useful and safe.
- [ ] Metrics/traces are considered when runtime behavior changes.
- [ ] Unit/integration/regression tests are considered.
- [ ] Validation commands are discovered from repo.
