# Backend Task Classification Example — API Design Routing

## User Request

"We need to add a new endpoint that lets customers update their subscription plan. Not sure how to model this or where the logic should live."

## Backend Task Classification

### Summary

This is a backend feature design task where the primary risk is unclear business workflow modeling — the subscription plan change is a state transition with billing implications, retry safety requirements, and customer ownership constraints.

### Task Type

- Backend feature design.
- Domain/API design.
- Application architecture analysis.
- Data/persistence analysis.
- Security/trust analysis.

### Primary Scope

`backend-domain-and-api-design`

Reason: the business workflow is unclear (what does "update subscription plan" mean — immediate switch, end-of-cycle, proration?), the API contract is undefined, and state transition semantics must be resolved before any implementation can proceed safely.

### Secondary Scopes

- `backend-application-architecture` — use-case orchestration, state machine for plan transitions, transaction boundaries, side effects (billing, notifications).
- `backend-data-and-persistence` — subscription state stored and queried; consistency required between plan state and billing records.
- `backend-security-and-trust` — customers must only update their own subscription; object-level authorization required.

### Cross-Cutting Concerns

| Concern          | Relevant? | Reason                                                              |
| ---------------- | --------: | ------------------------------------------------------------------- |
| Error handling   |       Yes | Billing errors must be separated from plan state errors             |
| Idempotency      |       Yes | Client retry on timeout must not trigger duplicate plan change      |
| Configuration    |  Possibly | Plan pricing and eligibility rules may be configurable              |
| Multi-tenancy    |        No | Single-tenant subscription model assumed unless stated otherwise    |
| Cost             |  Possibly | Billing API calls have cost implications                            |
| Governance       |  Possibly | Subscription changes may require audit trail for billing disputes   |
| Observability    |       Yes | Plan change events must be emitted and tracked                      |
| Privacy/security |       Yes | Subscription data is sensitive; authorization must be object-level  |
| Testing          |       Yes | State transition tests, auth tests, and idempotency tests required  |

### Risk Level

Medium.

### Risk Rationale

- Business workflow semantics (immediate vs deferred plan change) are unresolved.
- Billing side effects may not be reversible.
- Missing idempotency key could cause duplicate charges on retry.
- Object-level authorization must be enforced at the API layer.

### Context Needed

- Existing subscription domain model and state machine.
- Billing system API contract.
- Existing idempotency conventions.
- Customer authorization model.
- Error model conventions.
- Test harness and validation command.

### Recommended Specialized Skill

`backend-domain-and-api-design`

### Suggested Next Action

Clarify the business semantics of "update subscription plan" (immediate vs end-of-cycle, proration behavior, eligibility rules) and existing billing integration contract before designing the API.

### Handoff Prompt

```text
Use the backend-domain-and-api-design Skill.

Task:
Design a backend API for customers to update their subscription plan. The business
semantics of the plan change (immediate vs end-of-cycle, proration) and the billing
integration contract must be resolved as part of the design.

Primary scope:
backend-domain-and-api-design

Secondary scopes:
backend-application-architecture, backend-data-and-persistence, backend-security-and-trust

Risks:
- Business workflow semantics unresolved (immediate vs deferred).
- Billing side effects may not be reversible.
- Idempotency required for retry-safe plan changes.
- Object-level authorization required (customer can only change their own subscription).

Do not assume:
- A specific Java framework.
- Spring-specific transaction or event behavior.
- A specific billing provider API.
- Internal library behavior without repo evidence.

Expected output:
A framework-agnostic API design covering: domain state model, API contract,
error model, idempotency strategy, transaction boundary, billing side-effect
handling, authorization model, test plan, and observability considerations.
```
