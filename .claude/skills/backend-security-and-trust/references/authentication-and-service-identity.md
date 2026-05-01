# Authentication and Service Identity

## Purpose

Verify who the caller is before authorization decisions.

## Caller Types

- End user.
- Admin user.
- Service account.
- Background job.
- External provider webhook.
- Internal system.
- Anonymous caller.

## Questions

- How is identity established?
- Is the token/session/certificate verified?
- Is service-to-service identity required?
- Can identity be spoofed through headers?
- Are expired/revoked credentials rejected?
- Is authentication context propagated safely?

## Smells

- Trusting caller-provided user ID.
- Trusting internal network without identity.
- Accepting unsigned webhooks.
- Missing service identity for internal calls.
- Authentication context not available to authorization checks.
