---
purpose: Alert quality principles, bad alert anti-patterns, and runbook section guide for actionable on-call response
load-when: Reviewing existing alerts, designing new alerts, or drafting runbooks for a backend service
tier: domain
see-also:
  - slo-and-error-budgets.md
---

# Alerting and Runbooks

## Alert Principles

Good alerts are:

- User-impacting.
- Actionable.
- Owned.
- Low-noise.
- Linked to runbooks.
- Based on symptoms where possible.

## Bad Alerts

- Raw CPU alert without service impact.
- Expected validation error alert.
- Duplicate alerts for same incident.
- No owner.
- No mitigation path.
- Too sensitive thresholds causing noise.

## Runbook Sections

- Impact.
- Detection.
- Diagnosis.
- Mitigation.
- Rollback.
- Escalation.
- Safety warnings.
