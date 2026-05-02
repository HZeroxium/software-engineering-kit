# Runbook: <Service / Component Name>

## Overview

Describe what this runbook covers, what system or component it applies to, and when an operator would reach for it.

## Audience and Scope

- Intended audience: (on-call engineers / platform team / all engineers)
- Scope: (what is and is not covered)
- Prerequisites: (access, tools, credentials needed)

## Service Summary

Brief description of the service:

- Purpose:
- Dependencies:
- SLA / SLO:
- Ownership:

## Health Checks

Steps to verify the service is healthy before or after an incident:

- Check 1:
- Check 2:
- Expected signals (logs, metrics, dashboards):

## Common Incidents

### Incident: <Incident Name>

- **Symptoms**: What the operator observes.
- **Likely causes**: What typically triggers this.
- **Diagnosis steps**:
  1.
  2.
- **Resolution**:
  1.
  2.
- **Escalation**: When to escalate and to whom.
- **Post-incident**: What to document or follow up.

### Incident: <Incident Name>

- **Symptoms**:
- **Likely causes**:
- **Diagnosis steps**:
- **Resolution**:
- **Escalation**:
- **Post-incident**:

## Scheduled Operations

Operations that run on a schedule and may need manual intervention:

| Operation | Schedule | Owner | Notes |
|-----------|----------|-------|-------|
|           |          |       |       |

## Escalation Path

| Severity | Contact | Channel | SLA |
|----------|---------|---------|-----|
| P1 |  |  |  |
| P2 |  |  |  |
| P3 |  |  |  |

## Known Limitations and Caveats

-

## Related Links

- Dashboard:
- Alerts:
- Repo / service docs:
- Related runbooks:

## Validation Checklist

- [ ] All commands are verified from the repository (not invented).
- [ ] Incident procedures have been tested or reviewed by a team member.
- [ ] Escalation contacts are current.
- [ ] Known limitations are documented.
- [ ] Sensitive data (tokens, passwords, keys) is excluded.
- [ ] Last-updated date reflects recent review.
