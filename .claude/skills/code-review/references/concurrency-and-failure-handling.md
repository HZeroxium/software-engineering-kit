# Concurrency and Failure Handling Review

## Concurrency

Check:

- Shared mutable state is protected.
- Thread safety assumptions are valid.
- Async tasks do not access invalid lifecycle state.
- Locks are scoped and ordered correctly.
- Blocking calls are not used in event-loop/reactive paths.
- Transaction isolation is adequate.
- Lost updates are prevented.
- Double submit is safe.
- Duplicate message consumption is safe.
- Idempotency keys are handled correctly.

## Timeouts

Check:

- External calls have timeouts.
- Database calls are bounded where appropriate.
- Long-running operations are not hidden in request paths.
- Timeout errors are classified correctly.
- Timeout does not create duplicate side effects.

## Retries

Check:

- Retries are bounded.
- Retry only happens for retryable failures.
- Backoff and jitter are considered.
- Retry storms are avoided.
- Side effects are idempotent.
- Duplicate messages do not corrupt data.

## Partial Failure

Check:

- External dependency failure does not leave inconsistent state.
- Events are not emitted before durable state is committed unless intentional.
- Outbox or equivalent pattern is considered where appropriate.
- Compensation or rollback path exists.
- User-visible error is accurate.
- Observability captures failure cause.

## Resource Lifecycle

Check:

- Files, sockets, streams, clients, and DB resources are closed.
- Thread pools are bounded.
- Scheduled jobs are cancellable where needed.
- Background tasks are observable.
- Memory buffers are bounded.
- Connection pools are not leaked or exhausted.

## Review Output

For each finding:

- Describe the interleaving or failure scenario.
- Identify the unsafe state.
- Recommend the smallest fix.
- Recommend a deterministic test where possible.
