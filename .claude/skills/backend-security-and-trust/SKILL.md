---
name: backend-security-and-trust
description: Framework-agnostic backend Skill for authentication, authorization, object-level access control, tenant isolation, secrets, sensitive data, external calls, audit logs, abuse prevention, threat modeling, and API exposure.
---

# Backend Security and Trust

Use this Skill when a backend task involves authentication, authorization, object-level access, tenant isolation, secrets, sensitive data, external calls, audit logs, abuse prevention, threat modeling, or API exposure.

This Skill provides design and implementation guidance. Use a dedicated security reviewer agent, if available, for separate read-only security review.

## Purpose

Analyze backend security, identity, trust boundaries, abuse risk, and privacy-sensitive data flows.

This Skill covers:

- Trust boundary analysis.
- Authentication and service identity.
- Authorization model.
- Object-level and tenant access control.
- Sensitive data flow.
- Secrets and configuration risks.
- Input/output security.
- External call security.
- Abuse prevention.
- Audit logging.
- Security validation.

## Activation Criteria

Use when:

- A backend task involves authentication, authorization, or access control design.
- A PR or design introduces new API endpoints, permissions, roles, or trust boundaries.
- A task involves secrets, credentials, sensitive data, or external provider integration.
- A task requires input validation, output exposure review, or injection risk analysis.
- Threat modeling or security design review is requested.
- Abuse prevention, rate limiting, or audit logging is under discussion.

Do not use when:

- The task is a generic performance optimization with no security dimension.
- Pure infrastructure or network security without backend application logic is the scope.
- A dedicated security reviewer agent is available and a separate read-only review is sufficient.

## Required Inputs

| Input | Required? | Notes |
|-------|-----------|-------|
| Feature description or PR diff | Required | Minimum context for trust boundary analysis |
| Actor and identity model | Recommended | Who calls what: user, service, admin, background job |
| Existing authorization model | Recommended | RBAC/ABAC/ReBAC/custom, or unknown |
| Data sensitivity classification | If known | What data is sensitive, regulated, or secret |
| Tenant isolation requirements | If applicable | Single-tenant vs multi-tenant scope |
| External integration details | If affected | Third-party APIs, webhooks, or outbound calls |
| Existing security controls | If available | What auth/authz is already in place |

## Non-Goals

Do not:

- Assume Spring Security, OAuth library, IAM provider, API gateway, service mesh, or cloud security behavior.
- Invent organization-specific permission models.
- Print secrets.
- Treat authentication as sufficient authorization.
- Skip object-level access checks.
- Implement security-sensitive changes without approval.

## Workflow

1. Identify assets, actors, identities, and trust boundaries. See `references/owasp-api-security-risk-map.md`.
2. Identify authentication requirements. See `references/authentication-and-service-identity.md`.
3. Identify authorization model and object-level checks. See `references/authorization-models.md` and `references/object-level-and-tenant-access-control.md`.
4. Analyze tenant isolation. See `references/object-level-and-tenant-access-control.md`.
5. Trace sensitive data flow. See `checklists/privacy-and-sensitive-data-checklist.md`.
6. Review secrets and config risks. See `references/secrets-management.md`.
7. Review input/output security and external call trust. See `references/input-output-security.md` and `references/external-call-security.md`.
8. Identify abuse cases. See `references/abuse-prevention.md`.
9. Define audit logging requirements. See `references/audit-logging.md`.
10. Define manual review and validation plan.
11. Separate facts, assumptions, and unknowns.

## Expected Outputs

Output type: `mixed` — report (severity-ordered security findings), analysis (trust boundary and threat model), plan (audit logging plan, validation plan), checklist (security review checklist).

Primary template: `templates/backend-security-review.md`
Authorization review: `templates/authorization-boundary-review.md`
Audit logging: `templates/audit-logging-plan.md`
Sensitive data: `templates/sensitive-data-flow-review.md`
Threat model: `templates/threat-model-lite.md`

## Supporting files

Load only files whose "Load when" condition matches the current task. Do not load all files by default.

| File | Purpose | Load when |
|------|---------|-----------|
| `references/reference-index.md` | Semantic graph of all references: tiers, load order, navigation | Starting a task involving multiple security concerns, or unsure which references to load |
| `references/owasp-api-security-risk-map.md` | OWASP API top-10 risk taxonomy and backend review questions | Starting any backend security review — load first |
| `references/authorization-models.md` | Authorization model selection, decision guide, and common smells | Task involves authorization design, role/permission model, or access control review |
| `references/authentication-and-service-identity.md` | Authentication patterns, token validation, service-to-service identity | Task involves authentication, token/session validation, or service-to-service identity |
| `references/input-output-security.md` | Input injection risks and output exposure risks | Task involves input validation, injection risk, or API response exposure |
| `references/object-level-and-tenant-access-control.md` | Object ownership verification and tenant isolation checks | Task involves resource ownership, tenant isolation, or multi-tenant data access |
| `references/secrets-management.md` | Secrets handling rules, review questions, and common smells | Task involves credentials, API keys, tokens, certificates, or sensitive config |
| `references/abuse-prevention.md` | Abuse controls — rate limiting, quotas, replay protection | Abuse risk detected: public APIs, expensive operations, or replay-vulnerable flows |
| `references/audit-logging.md` | Audit event design and required fields | Task involves security-relevant logging, accountability, or compliance |
| `references/external-call-security.md` | Outbound HTTP, webhook validation, third-party API trust | Task involves outbound calls, SSRF risk, webhook handlers, or third-party integration |
| `checklists/backend-security-checklist.md` | Full security review checklist | Starting a comprehensive security review |
| `checklists/authorization-checklist.md` | Authorization-specific checklist | Authorization design or review is the primary focus |
| `checklists/abuse-risk-checklist.md` | Abuse risk checklist | Abuse or rate limiting is under review |
| `checklists/privacy-and-sensitive-data-checklist.md` | Privacy and sensitive data checklist | Sensitive data flow or privacy review is needed |
| `templates/backend-security-review.md` | Full security review output template | Producing a comprehensive security review |
| `templates/authorization-boundary-review.md` | Authorization boundary review template | Authorization boundary or access control review |
| `templates/audit-logging-plan.md` | Audit logging plan template | Designing or reviewing audit logging |
| `templates/sensitive-data-flow-review.md` | Sensitive data flow review template | Sensitive data flow analysis |
| `templates/threat-model-lite.md` | Lightweight threat model template | Threat modeling or trust boundary analysis |
| `examples/java-authorization-review-example.md` | Java example: object-level authorization finding and fix | Reviewing Java code with missing authorization checks |
| `examples/java-backend-security-examples.md` | Java sketches for authorization check and audit event patterns | Requesting Java code examples for security implementation |

## Safety Boundaries

Require human approval before:

- Changing authorization behavior.
- Changing tenant isolation.
- Handling secrets or credentials.
- Logging sensitive data.
- Modifying security config.
- Changing authentication/session/token behavior.
- Exposing new public APIs.
- Sending data to external providers.

## Failure handling

If required inputs are incomplete:

- State what was reviewed and what could not be verified.
- Mark findings as evidence-based or assumption-based.
- Do not invent authorization models, data sensitivity classifications, or security controls.
- Recommend the smallest next context sample needed (diff, module, existing auth code).
- Flag gaps as open questions rather than resolving them silently.

## Maintenance

- Owner: User-global, self-maintained.
- Update triggers: OWASP API Security list updates; new backend security patterns emerge; repeated misclassification of security findings; new trust boundary or identity pattern identified; abuse vector not covered by existing checklists.
- Deprecation condition: If replaced by a more specialized security review skill covering compliance, infrastructure, or regulatory domains.
