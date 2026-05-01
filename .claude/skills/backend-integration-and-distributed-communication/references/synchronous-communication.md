# Synchronous Communication

## Purpose

Use synchronous communication when the caller needs an immediate response and the dependency can meet the latency/reliability requirements.

## Common Forms

- HTTP APIs.
- RPC.
- Internal service APIs.
- SDK/client library calls.
- External provider APIs.

## Design Questions

- Does the caller need an immediate result?
- What is the timeout?
- Is there a caller deadline?
- Is retry safe?
- What happens if the dependency is slow?
- What errors are returned to the caller?
- Is fallback possible?

## Failure Modes

- Missing timeout.
- Retrying non-idempotent operation.
- Dependency latency consumes request budget.
- Error mapping hides dependency failure.
- Caller blocks on slow workflow that should be async.
