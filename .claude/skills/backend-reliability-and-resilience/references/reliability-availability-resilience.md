# Reliability, Availability, and Resilience

## Definitions

- **Reliability:** The system performs correctly from the user’s perspective.
- **Availability:** The system can serve requests.
- **Resilience:** The system can absorb, recover from, or degrade under failure.
- **Durability:** Committed data is not lost.
- **Recoverability:** The system can be restored after failure.

## Review Questions

- What does user-visible correctness mean?
- What failures are acceptable?
- What dependencies can fail?
- What degraded mode is acceptable?
- How does the system recover?
- How do operators know users are affected?

## Failure Modes

- Internal checks pass but users fail.
- Retry causes more outage load.
- No fallback for dependency failure.
- Backup exists but restore is untested.
- Alerts fire on symptoms no one needs to act on.
