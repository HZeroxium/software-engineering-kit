# Error Models

## Purpose

Design errors that are stable, actionable, safe, and observable.

## Error Dimensions

- Business vs technical.
- Retryable vs non-retryable.
- User-facing vs internal.
- Field-level vs operation-level.
- Permanent vs transient.
- Expected vs unexpected.

## Error Design Principles

- Use stable machine-readable codes.
- Keep user-facing message safe.
- Preserve enough detail for client action.
- Avoid stack traces and internal details.
- Include correlation IDs if repository conventions support them.
- Map dependency failures carefully.
- Do not use one generic error for all failures.

## Common Error Categories

- Validation error.
- Authentication required.
- Forbidden.
- Not found.
- Conflict.
- Rate limited.
- Dependency unavailable.
- Timeout.
- Internal error.

## Review Smells

- Raw exception messages returned.
- Inconsistent status mapping.
- Validation details missing.
- Retryability unclear.
- Business errors logged as system errors.
- Sensitive data in error messages.
