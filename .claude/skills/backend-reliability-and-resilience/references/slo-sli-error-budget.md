# SLO, SLI, and Error Budget

## SLI

A service-level indicator measures service behavior, such as availability, latency, error rate, freshness, or backlog.

## SLO

A service-level objective sets the target for an SLI over a time window.

## Error Budget

The allowed amount of unreliability during the SLO window.

## Good SLIs

- User-impacting.
- Measurable.
- Actionable.
- Stable enough to alert on.
- Tied to a critical journey.

## Bad SLIs

- Internal-only symptom with no user impact.
- Raw CPU or memory without service context.
- Metrics with unclear ownership.
- Too many SLIs for one service.

## Review Questions

- What is the critical user journey?
- What is a good event?
- What is a bad event?
- What window matters?
- What action follows budget burn?
