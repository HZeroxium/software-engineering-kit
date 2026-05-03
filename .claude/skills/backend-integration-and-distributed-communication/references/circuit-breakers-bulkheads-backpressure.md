---
purpose: Circuit breaker, bulkhead, and backpressure patterns for protecting service reliability under dependency failure or overload
load-when: Dependency failures are frequent, resource pools are shared, consumer lag is detected, or external rate limiting is encountered
tier: scenario
see-also: []
---

# Circuit Breakers, Bulkheads, and Backpressure

## Circuit Breaker

Temporarily stop calling unhealthy dependencies to reduce cascading failure.

Use when:

- Dependency failures are frequent.
- Calls are expensive or slow.
- Fallback behavior exists.
- Failure rate can be measured.

## Bulkhead

Isolate resources so one dependency or tenant cannot exhaust all capacity.

Use when:

- Shared thread/connection pools create cascading risk.
- Dependencies have different reliability profiles.
- Tenant or workload isolation matters.

## Backpressure

Slow or reject work when the system cannot safely process more.

Use when:

- Queues grow unbounded.
- Consumers lag.
- External providers rate-limit.
- Work is expensive.

## Review Questions

- What resource is isolated?
- What is the fallback?
- What signal opens the circuit?
- What work is rejected vs queued?
- How is overload visible to operators?
