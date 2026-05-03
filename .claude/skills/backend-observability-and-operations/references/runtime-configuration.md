---
purpose: Environment config, secrets separation, feature flags, kill switches, config validation, and auditability for backend services
load-when: Change adds or modifies runtime configuration, feature flags, kill switches, or environment-specific behavior
tier: scenario
see-also: []
---

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
