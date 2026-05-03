# SLO Breach and Incident Triage Example

## Scenario

A checkout service has a 99.5% availability SLO (rolling 28 days). An alert fires: availability has dropped to 98.1% over the last hour. Error budget burn rate is 7×.

## Finding

The payment gateway dependency is returning HTTP 503 with no retry-after header. The service retries three times with no jitter and no circuit breaker. Retry storms amplify load on the gateway during its recovery window.

## Risk

- **Severity:** Critical.
- **Failure mode:** Retry storm prevents gateway recovery; checkout availability continues to degrade.
- **SLO impact:** At 7× burn rate, the 28-day error budget exhausts in ~4 days. Release freeze threshold is imminent.

## Immediate Mitigation

1. Enable circuit breaker on payment gateway client — stop retrying while gateway is unhealthy.
2. Add exponential backoff with jitter to remaining retries.
3. Return user-visible "payment temporarily unavailable" response (graceful degradation) instead of hanging.

## Incident Readiness Gaps Found

- No runbook for payment gateway outage — diagnosis steps were improvised.
- No alert on payment error rate specifically — SLO availability alert was the only signal.
- Rollback path: feature flag to disable payment gateway retries was not pre-wired.

## Validation

- Circuit breaker transition test (closed → open → half-open → closed).
- Retry exhaustion test with jitter verification (check retry intervals are not synchronized).
- Fallback response test under gateway 503.
- SLO burn rate dashboard review after mitigation.
- Runbook drafted and reviewed by on-call rotation.
