---
purpose: Test types for verifying failure behavior (timeout, retry, circuit breaker, bulkhead, failover, duplicate delivery); safety constraints for destructive tests
load-when: Designing or reviewing resilience tests, chaos tests, or failure injection scenarios
tier: domain
see-also: []
---

# Resilience Testing

## Purpose

Verify behavior under failure instead of assuming resilience.

## Test Types

- Timeout test.
- Dependency error test.
- Retry exhaustion test.
- Circuit breaker transition test.
- Bulkhead saturation test.
- Backpressure test.
- Failover test.
- Restore test.
- Queue backlog test.
- Duplicate delivery test.

## Questions

- What failure is injected?
- What user-visible behavior is expected?
- What telemetry proves detection?
- What recovery is expected?
- Is the test deterministic and safe?

## Safety

Do not run destructive or production-impacting resilience tests without approval.
