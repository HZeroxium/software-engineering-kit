---
purpose: Authentication patterns, token validation checklist, and service-to-service identity options
load-when: Task involves authentication, token/session validation, or service-to-service identity
tier: domain
see-also: []
---

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

## Token Validation Checklist

- [ ] Signature verified using the expected algorithm and key.
- [ ] Expiry (`exp`) checked — reject expired tokens.
- [ ] Issuer (`iss`) verified — reject tokens from unexpected issuers.
- [ ] Audience (`aud`) verified — reject tokens not intended for this service.
- [ ] Not-before (`nbf`) checked when present.
- [ ] Revocation check applied where required (short-lived tokens or logout-sensitive flows).
- [ ] Token type (`typ`) checked when multiple token types are in use.

## Service-to-Service Identity Options

| Pattern | Description | Risk |
|---------|-------------|------|
| Shared secret header | Simple internal header with pre-shared secret | Spoofable if network is compromised; requires secret rotation |
| Signed JWT (service token) | Service presents a signed JWT verified by the recipient | Key management required; clock skew must be handled |
| mTLS | Certificate-based mutual auth at transport layer | Infrastructure complexity; strongest assurance |
| Platform identity (IRSA, Workload Identity, SPIFFE) | Cloud or mesh-native identity without explicit credentials | Platform lock-in; preferred when available |

Choose based on the organization's existing identity infrastructure. Document the chosen pattern explicitly.
