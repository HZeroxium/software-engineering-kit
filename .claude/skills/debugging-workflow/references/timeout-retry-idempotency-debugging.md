---
purpose: Timeout, retry, retry storm, duplicate side effect, and idempotency analysis
load-when: Debugging hangs, timeouts, retries, duplicate side effects, retry storms, or idempotency gaps
tier: scenario
see-also: []
---

# Timeout, Retry, and Idempotency Debugging

## Timeout Symptoms

- Requests hang.
- CI times out.
- External call fails intermittently.
- Latency spikes.
- Thread pool saturation.
- Queue lag grows.
- Duplicate side effects after client retry.

## Retry Symptoms

- Repeated calls to dependency.
- Duplicate records.
- Duplicate notifications.
- Retry storm during outage.
- Increased load after partial failure.
- Logs show repeated same operation.

## Idempotency Symptoms

- Same user action creates duplicate state.
- Same message processed multiple times.
- Retry changes result.
- Timeout leaves unknown state.
- Duplicate payment/order/notification.

## Evidence to Inspect

- Timeout settings.
- Retry policy.
- Backoff and jitter.
- Error classification.
- Idempotency key.
- Unique constraints.
- Transaction boundaries.
- External dependency behavior.
- Logs with request IDs.
- Metrics for retry count and timeout count.

## Debug Questions

- Which operations are safe to retry?
- Which failures are retryable?
- Is retry bounded?
- Is backoff used?
- Is jitter used?
- Can the same request be processed twice?
- What is the source of truth for completion?
- What happens if timeout occurs after side effect succeeds?
- What happens when message is redelivered?

## Fix Patterns

- Add bounded timeout.
- Add retry only for retryable errors.
- Add backoff and jitter.
- Add idempotency key.
- Add unique constraint.
- Store operation status.
- Use outbox pattern where appropriate.
- Add metrics for retries/timeouts.
- Add regression test for duplicate retry.
