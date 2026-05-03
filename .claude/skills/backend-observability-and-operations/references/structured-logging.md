---
purpose: Structured log field design, sensitive-data avoidance rules, and common logging smells to detect in review
load-when: Reviewing or planning logging for a backend change
tier: domain
see-also: []
---

# Structured Logging

## Purpose

Make logs searchable, correlated, safe, and useful.

## Useful Fields

- Timestamp.
- Level.
- Event name.
- Correlation/request ID.
- Operation.
- Outcome.
- Error category.
- Duration.
- Safe resource identifier.
- Safe actor/tenant identifier if policy allows.

## Avoid

- Secrets.
- Tokens.
- Passwords.
- Raw payloads.
- PII without policy.
- Stack traces for expected business errors.
- Unbounded field values.

## Review Smells

- Free-form logs only.
- Missing correlation ID.
- Sensitive data in logs.
- Error logs for expected validation failures.
- No log on important state transition.
