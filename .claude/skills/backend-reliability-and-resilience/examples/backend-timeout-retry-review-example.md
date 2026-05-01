# Backend Timeout / Retry Review Example

## Scenario

A backend API calls an external document analysis provider synchronously.

## Finding

The code retries provider calls three times without an explicit timeout and without idempotency guarantees.

## Risk

- **Severity:** High.
- **Failure mode:** Provider slowdown causes request pileups; retry may duplicate provider work and increase cost.
- **User impact:** API latency spikes or fails under dependency degradation.

## Minimal Fix

- Add bounded timeout.
- Retry only retryable transient failures.
- Use provider idempotency key if external work may be duplicated.
- Consider async job flow if provider latency exceeds request budget.

## Validation

- Timeout test.
- Retry exhaustion test.
- Duplicate/idempotency test.
- Metrics/log review for timeout and retry outcomes.
