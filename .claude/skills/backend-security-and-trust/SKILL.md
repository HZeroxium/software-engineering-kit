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

## Non-Goals

Do not:

- Assume Spring Security, OAuth library, IAM provider, API gateway, service mesh, or cloud security behavior.
- Invent organization-specific permission models.
- Print secrets.
- Treat authentication as sufficient authorization.
- Skip object-level access checks.
- Implement security-sensitive changes without approval.

## Workflow

1. Identify assets, actors, identities, and trust boundaries.
2. Identify authentication requirements.
3. Identify authorization model and object-level checks.
4. Analyze tenant isolation.
5. Trace sensitive data flow.
6. Review secrets and config risks.
7. Review input/output security.
8. Identify abuse cases.
9. Define audit logging requirements.
10. Define manual review and validation plan.
11. Separate facts, assumptions, and unknowns.

## Expected Output

Return:

- Trust boundary analysis.
- Authentication and authorization model.
- Object-level/tenant access control checks.
- Sensitive data flow.
- Secrets and config risks.
- Input/output security risks.
- Abuse cases.
- Audit logging plan.
- Manual review requirements.
- Security validation plan.

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
