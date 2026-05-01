# Human-in-the-Loop and Approval Boundaries

## Purpose

Define where humans must approve AI-assisted backend decisions and actions.

## Require Approval For

- Production mutations.
- Database migrations.
- Data deletion.
- Security-sensitive changes.
- Permission or role changes.
- External system writes.
- Tool calls with side effects.
- Sending sensitive data to external providers.
- Dependency or model provider changes.
- Compliance or policy exceptions.
- High-cost batch AI jobs.
- Automated user-facing communication when risk is high.

## Approval Record

Capture:

- Who approved.
- What was approved.
- Why it was approved.
- Scope and limits.
- Timestamp.
- Related ticket/PR/incident.
- Rollback or disable path.

## Failure Modes

- Approval is implied but not explicit.
- Approval lacks scope.
- Tool performs more than approved.
- Audit record missing.
- Human review occurs after irreversible action.
