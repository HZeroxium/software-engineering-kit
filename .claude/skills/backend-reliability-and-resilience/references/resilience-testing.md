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
