# Runtime Configuration

## Purpose

Configure behavior safely across environments.

## Review Areas

- Environment-specific config.
- Secrets separation.
- Feature flags.
- Kill switches.
- Rate limits.
- Timeouts.
- Retry limits.
- Dynamic config.
- Validation at startup.
- Auditability.

## Questions

- Are defaults safe?
- Is config validated?
- Can config be changed safely?
- Is production config reviewed?
- Are secrets logged or exposed?
- Is rollback possible through config?
