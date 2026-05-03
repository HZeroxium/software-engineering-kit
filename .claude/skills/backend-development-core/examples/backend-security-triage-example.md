# Backend Task Classification Example — Security Triage

## User Request

"Add an admin API endpoint that lets support staff view and update any customer's profile data."

## Backend Task Classification

### Summary

This is a backend feature design task with Critical security risk: it introduces a privileged admin access path that bypasses normal customer ownership boundaries, requiring object-level authorization design, audit logging, and human approval before implementation.

### Task Type

- Backend feature design.
- Security/trust analysis.
- Domain/API design.
- Observability/operations analysis.

### Primary Scope

`backend-security-and-trust`

Reason: the defining risk is privileged access to arbitrary customer data. This requires explicit admin role design, object-level authorization checks, audit logging of all access and mutations, and careful API design to prevent accidental over-exposure of sensitive fields.

### Secondary Scopes

- `backend-domain-and-api-design` — admin API contract, admin-specific error model, sensitive field visibility rules.
- `backend-observability-and-operations` — audit log design, alert on privileged access, operational runbook for support workflows.

### Cross-Cutting Concerns

| Concern          | Relevant? | Reason                                                                      |
| ---------------- | --------: | --------------------------------------------------------------------------- |
| Error handling   |       Yes | Admin errors must not leak customer data in error responses                 |
| Idempotency      |        No | Admin profile reads are idempotent by nature; updates should be standard    |
| Configuration    |       Yes | Admin role assignment and scope must be configurable and auditable           |
| Multi-tenancy    |  Possibly | If multi-tenant, admin access must be scoped to the correct tenant           |
| Cost             |        No | No unusual cost implications                                                 |
| Governance       |       Yes | Data access policy and admin access approval required                        |
| Observability    |       Yes | Every admin access and mutation must produce an audit log entry              |
| Privacy/security |       Yes | PII in profile responses; admin scope must be minimized to fields needed     |
| Testing          |       Yes | Authorization tests, negative tests (non-admin denied), audit log assertions |

### Risk Level

Critical.

### Risk Rationale

- Admin endpoint bypasses normal customer ownership authorization.
- Sensitive customer PII may be exposed or mutated.
- Missing audit trail is a compliance and incident-response gap.
- Incorrect role check could allow any authenticated user to access any profile.
- Admin mutations without audit logging create unattributable data changes.

### Requires Human Approval

Yes — before implementation begins:
- Data governance team approval for admin access scope.
- Security review of authorization model.
- Definition of which profile fields are accessible/mutable by support staff.

### Context Needed

- Existing admin role model and authentication mechanism.
- Customer profile data model and field sensitivity classification.
- Existing audit logging infrastructure.
- Data access policy and PII classification.
- Existing API authorization patterns (object-level checks).
- Test harness and validation command.

### Recommended Specialized Skill

`backend-security-and-trust`

### Suggested Next Action

Do not implement. First: define the admin role scope (which staff, what access level), enumerate which profile fields are viewable vs mutable, confirm audit logging infrastructure, and obtain data governance approval.

### Handoff Prompt

```text
Use the backend-security-and-trust Skill.

Task:
Design an admin API endpoint for support staff to view and update customer profile data.
Risk level is Critical. Human approval required before implementation.

Primary scope:
backend-security-and-trust

Secondary scopes:
backend-domain-and-api-design, backend-observability-and-operations

Risks:
- Privileged admin access bypassing customer ownership authorization.
- Sensitive PII exposure in responses.
- Missing audit trail for privileged access and mutations.
- Incorrect role check granting unauthorized access.
- Admin mutations without attribution.

Do not assume:
- A specific Java framework.
- An existing admin role system without repo evidence.
- Internal library authorization conventions without confirmation.
- Any specific PII classification without data governance input.

Constraints:
- Do not proceed to implementation plan until human approval is confirmed.
- Authorization design must include object-level checks, not just role checks.
- Audit log must record: actor identity, action, target resource, timestamp, and outcome.
- Minimize field exposure — only fields needed for support workflows.

Expected output:
A security-first design covering: admin role model, authorization boundary,
object-level access control, sensitive field exposure policy, audit log design,
API contract, test strategy (authorization tests, negative tests, audit assertions),
governance approval gates, and observability plan.
```
