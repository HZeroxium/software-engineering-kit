---
purpose: Design principles and failure modes for timeout, retry, circuit breaker, and bulkhead controls; jitter, exponential backoff, deadline propagation, and idempotency key patterns
load-when: Reviewing or designing timeout, retry, circuit breaker, or bulkhead behavior for a dependency
tier: domain
see-also:
  - load-shedding-and-backpressure.md
---

# Timeout, Retry, Circuit Breaker, and Bulkhead

## Timeout

Every remote dependency needs bounded wait time.

## Retry

Retry only transient failures and only when safe.

## Circuit Breaker

Stop calling unhealthy dependencies temporarily to reduce cascading failure.

## Bulkhead

Isolate resources so one failing dependency or workload cannot exhaust all capacity.

## Review Questions

- Is timeout shorter than caller deadline?
- Is retry bounded?
- Is the operation idempotent?
- Is there fallback when circuit opens?
- Are resource pools isolated?
- Is overload visible?

## Failure Modes

- No timeout.
- Retry storm.
- Circuit opens but no fallback.
- Shared pool starvation.
- Bulkhead too small for normal traffic.

## Exponential Backoff and Jitter

Without jitter, retries from many callers synchronize and amplify load on a recovering dependency.

- Base interval doubles on each attempt up to a cap.
- Add random jitter (full or equal jitter) to desynchronize callers.
- Decorrelated jitter (`sleep = random(base, prev_sleep * 3)`) is effective under high concurrency.

## Deadline Propagation

A timeout on a single call is insufficient if callers do not propagate the remaining deadline.

- Record deadline at the entry point (e.g., HTTP request received time + SLA budget).
- Pass remaining deadline downstream via context or header.
- Abort outbound calls that exceed remaining deadline before sending.
- Prevents cascading timeouts that waste capacity on doomed requests.

## Idempotency Key

Required when retry may duplicate side effects on an external dependency.

- Generate a stable key per logical operation (not per attempt).
- Include key in request header or body.
- Key must survive retries but differ across independent operations.
- Verify the dependency honors the key before enabling retries.

## Review Questions (Extended)

- Is jitter applied to prevent retry synchronization?
- Is deadline propagated from entry point to all outbound calls?
- Does the operation have a stable idempotency key for retries?
- What is the total timeout budget across the call chain?
