# Auditability and Policy Enforcement

## Purpose

Ensure important backend decisions and actions are enforceable, reviewable, and traceable.

## Auditability

Auditability answers:

- Who did what?
- To which resource?
- When?
- Under which policy or approval?
- What was the result?
- Can the evidence be reviewed later?

## Policy Enforcement

Policy enforcement should be:

- Explicit.
- Testable.
- Close to the trust boundary.
- Consistent across API, worker, and tool paths.
- Auditable for privileged actions.

## Examples of Auditable Events

- Permission change.
- Sensitive data access.
- Admin action.
- AI tool side effect.
- Data export.
- Model/provider configuration change.
- Policy override.
- Human approval decision.

## Review Smells

- Policy exists only in documentation.
- Privileged paths skip audit.
- Background jobs bypass access rules.
- AI tools mutate state without approval record.
- Logs include sensitive payloads instead of safe audit metadata.
