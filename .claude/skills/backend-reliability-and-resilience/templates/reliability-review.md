# Reliability Review

## Summary

- **System / feature:** `<name>`
- **User-visible journey:** `<journey>`
- **Risk level:** `<low/medium/high/critical>`
- **Recommendation:** `<approve / revise / block>`

## User-Visible Reliability Target

`<target or unknown>`

## Critical Dependencies

| Dependency     | Role     | Failure Impact | Mitigation     |
| -------------- | -------- | -------------- | -------------- |
| `<dependency>` | `<role>` | `<impact>`     | `<mitigation>` |

## Failure Modes

| Failure     | User Impact | Current Behavior | Recommended Behavior |
| ----------- | ----------- | ---------------- | -------------------- |
| `<failure>` | `<impact>`  | `<behavior>`     | `<recommendation>`   |

## Resilience Controls

| Control         |           Present? | Notes     |
| --------------- | -----------------: | --------- |
| Timeout         | `<yes/no/unknown>` | `<notes>` |
| Retry limit     | `<yes/no/unknown>` | `<notes>` |
| Circuit breaker | `<yes/no/unknown>` | `<notes>` |
| Bulkhead        | `<yes/no/unknown>` | `<notes>` |
| Backpressure    | `<yes/no/unknown>` | `<notes>` |
| Fallback        | `<yes/no/unknown>` | `<notes>` |
| Idempotency     | `<yes/no/unknown>` | `<notes>` |

## SLO / SLI

- **SLI candidates:** `<availability, latency, error rate, freshness, backlog, etc.>`
- **SLO target:** `<target or unknown>`
- **Error budget implication:** `<notes>`

## Incident Readiness

- **Alert:** `<yes/no/unknown>`
- **Runbook:** `<yes/no/unknown>`
- **Rollback:** `<yes/no/unknown>`
- **Owner:** `<owner/unknown>`

## Validation

- `<failure-mode test>`
- `<timeout test>`
- `<fallback test>`
- `<manual incident review>`
