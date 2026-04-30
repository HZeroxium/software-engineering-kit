# Concurrency and Async

## General Questions

- What runs concurrently?
- What state is shared?
- What operations are retryable?
- What operations are idempotent?
- What are the timeout boundaries?
- What happens on cancellation?
- What happens on partial failure?
- What resources must be closed?

## Java

- Avoid unsafe shared mutable state.
- Use thread-safe types only when they fit the access pattern.
- Bound executors and queues.
- Avoid blocking event-loop/reactive threads.
- Use timeouts for external calls.
- Preserve interruption where applicable.
- Close resources with try-with-resources.
- Make transaction boundaries clear.

## Python

- Do not block inside async functions.
- Await async operations.
- Use timeouts for I/O.
- Bound concurrent tasks.
- Handle cancellation where relevant.
- Avoid unobserved background tasks.
- Protect shared mutable state.

## TypeScript

- Await promises or intentionally handle detached work.
- Use AbortController or project-standard cancellation where applicable.
- Handle rejected promises.
- Avoid shared mutable module state in concurrent request paths.
- Avoid retrying non-idempotent operations.
- Manage loading/error state in UI flows.

## Failure Handling

- Bound retries.
- Use backoff for transient failures.
- Avoid retry storms.
- Preserve cause and context.
- Make duplicate processing safe.
- Add metrics/logs for timeouts and retries when production-relevant.
