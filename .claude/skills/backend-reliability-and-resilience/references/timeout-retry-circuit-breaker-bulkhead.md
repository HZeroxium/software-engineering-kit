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
