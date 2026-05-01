# Audit Logging

## Purpose

Record security-relevant actions for accountability and investigation.

## Audit When

- Login/logout/session changes.
- Permission changes.
- Admin actions.
- Sensitive data access.
- Resource create/update/delete.
- Security policy decisions.
- External data sharing.
- Failed authorization for sensitive actions.

## Audit Fields

- Actor.
- Action.
- Resource.
- Decision/result.
- Timestamp.
- Correlation ID.
- Source system.
- Tenant/context when safe.
- Reason/policy where useful.

## Avoid

- Secrets.
- Full tokens.
- Sensitive payloads.
- Unbounded request bodies.
- Data that violates privacy policy.
