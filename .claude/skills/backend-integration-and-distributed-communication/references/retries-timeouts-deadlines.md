# Retries, Timeouts, and Deadlines

## Purpose

Prevent slow dependencies, retry storms, and unsafe duplicate side effects.

## Rules

- Every remote call needs a timeout or deadline.
- Retries require retryable failure classification.
- Retried operations must be idempotent or safely deduplicated.
- Use bounded retries.
- Prefer backoff and jitter for retryable transient failures.
- Propagate caller deadlines where supported.
- Do not retry permanent business errors.

## Review Questions

- What is the total request budget?
- What is the per-dependency timeout?
- Which errors are retryable?
- What is the retry limit?
- Can retry overload the dependency?
- What happens if success occurs but response is lost?

## Failure Modes

- Infinite retry loop.
- Retry storm during outage.
- Timeout longer than caller deadline.
- Duplicate write.
- Retrying validation or authorization errors.
