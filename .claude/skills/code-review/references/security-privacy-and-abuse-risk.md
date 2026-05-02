---
purpose: Security, privacy, abuse risk, and reliability review checks
load-when: Reviewing auth, permissions, input/output safety, secrets, privacy, abuse, or reliability-sensitive changes
tier: domain
see-also: []
---

# Security, Privacy, Abuse Risk, and Reliability Review

## Authentication and Authorization

Check:

- Authentication is required where needed.
- Authorization is checked at the correct boundary.
- Ownership and tenant boundaries are enforced.
- Admin-only actions are protected.
- Object-level access control is present.
- Authorization is not only enforced in the UI.
- Role/status changes are handled safely.
- Default behavior is deny, not allow.

## Input Validation and Injection

Check:

- User input is validated.
- Server-side validation exists.
- SQL/NoSQL queries are parameterized or safely constructed.
- Shell commands are not built from unsanitized input.
- Path traversal is prevented.
- SSRF risk is considered for URLs.
- Deserialization is safe.
- File upload type, size, and path are controlled.
- Regex usage cannot cause catastrophic backtracking.

## Secrets and Sensitive Data

Check:

- No secrets are committed.
- No secrets are logged.
- No credentials are sent to clients.
- No tokens are exposed in URLs.
- Sensitive data is redacted in logs.
- Error responses do not leak internals.
- Test fixtures do not contain real secrets.
- Config defaults are safe.

## Privacy

Check:

- Only necessary data is collected and returned.
- Sensitive fields are excluded from responses and notifications.
- Logs avoid customer data and personal data.
- Data retention and deletion behavior are respected.
- Cross-user data leakage is not possible.
- Export/download features enforce permissions and scope.

## Abuse Risk

Check:

- Rate limiting or throttling is considered where needed.
- Expensive operations cannot be abused.
- Retry behavior cannot amplify load.
- Public endpoints cannot enumerate resources.
- Search/export endpoints have limits.
- Notification/email flows cannot spam users.
- Business workflow cannot be bypassed.

## Reliability

Check:

- Dependency failures are handled.
- Timeouts exist.
- Retries are bounded and safe.
- Circuit breaking or fallback is considered when relevant.
- Failures are observable.
- Critical operations are idempotent where retries are possible.
