# Release and Rollback Readiness

## Purpose

Ensure backend changes can be deployed and reverted safely.

## Review Questions

- Is change backward compatible?
- Are migrations expand-contract safe?
- Can old and new versions run together?
- Is rollback safe after data changes?
- Is feature flag or kill switch needed?
- Are dashboards/alerts ready?
- Is runbook updated?

## Failure Modes

- Rollback breaks after schema change.
- Feature cannot be disabled.
- Release depends on manual undocumented steps.
- No visibility after rollout.
- Alert noise during release.
