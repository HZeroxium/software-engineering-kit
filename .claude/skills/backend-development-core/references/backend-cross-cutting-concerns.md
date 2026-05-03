---
purpose: 9 cross-cutting backend concerns (error handling, idempotency, configuration, multi-tenancy, cost, governance, observability, privacy, testing) that apply across all scopes
load-when: Task triage reveals multiple overlapping scopes or cross-cutting risk signals are present
tier: domain
see-also:
  - backend-failure-modes.md
---

# Backend Cross-Cutting Concerns

## Purpose

Cross-cutting concerns appear across many backend scopes. Always check them during task triage, even when they are not the primary scope.

## 1. Error Handling

### Applies To

- API design.
- Application architecture.
- Distributed communication.
- Reliability.
- Observability.
- Testing.

### Questions

- Is this a business error or technical error?
- Is it retryable?
- Should the user see it?
- Should it be logged?
- Should it trigger an alert?
- Does it require compensation?
- Does the API expose stable error codes?

### Failure Modes

- Inconsistent error shapes.
- Retrying non-retryable errors.
- Leaking internal errors to users.
- Missing correlation IDs.
- Swallowing exceptions.
- Alerting on expected business errors.

## 2. Idempotency

### Applies To

- API design.
- Messaging.
- Retries.
- Payments/order-like workflows.
- Background jobs.
- Distributed systems.
- Data persistence.

### Questions

- Can the operation be safely retried?
- Is there an idempotency key?
- What is the deduplication window?
- What state is returned on duplicate requests?
- Are consumers idempotent?
- Is exactly-once delivery being assumed incorrectly?

### Failure Modes

- Duplicate records.
- Double charges.
- Duplicate notifications.
- Non-idempotent retries.
- Consumer side effects repeated after redelivery.

## 3. Configuration

### Applies To

- Application architecture.
- Security.
- Operations.
- Reliability.
- Testing.
- Deployment.

### Questions

- Which config is environment-specific?
- Which config is secret?
- Are defaults safe?
- Is config validated at startup?
- Can config change dynamically?
- Is config auditable?

### Failure Modes

- Secrets in source code.
- Production config changed without review.
- Missing config validation.
- Unsafe defaults.
- Environment drift.

## 4. Multi-Tenancy

### Applies To

- Security.
- Data.
- Performance.
- Observability.
- Governance.

### Questions

- How is tenant identity established?
- Is tenant isolation enforced at API, application, and data layers?
- Are tenant IDs included in audit logs?
- Are metrics tenant-aware without excessive cardinality?
- Are noisy-neighbor controls needed?

### Failure Modes

- Cross-tenant data access.
- Missing tenant filter in queries.
- Shared caches leaking data.
- Tenant ID spoofing.
- Unbounded tenant-level cardinality.

## 5. Cost

### Applies To

- Performance.
- Operations.
- Observability.
- Data.
- AI systems.
- External integrations.

### Questions

- What is the cost per request, tenant, job, or workflow?
- Which component dominates cost?
- Are logs, traces, or metrics too expensive?
- Are AI token/model costs monitored?
- Can cheaper execution preserve quality?

### Failure Modes

- Overprovisioning.
- Excessive telemetry cost.
- Expensive queries.
- Unbounded AI calls.
- Retry storms increasing provider bills.

## 6. Governance

### Applies To

- Security.
- Data.
- AI.
- Operations.
- Architecture.

### Questions

- Who owns the service and data?
- Which decisions require approval?
- Are ADRs needed?
- Are compliance controls testable?
- Is vendor risk understood?
- Is risk accepted or mitigated?

### Failure Modes

- No ownership.
- Unreviewed architecture decisions.
- Missing audit evidence.
- Compliance treated after release.
- Undocumented exceptions.

## 7. Observability

### Applies To

- All production backend work.

### Questions

- Can we detect failure?
- Can we diagnose failure?
- Can we correlate logs, metrics, and traces?
- Are signals user-impacting?
- Are sensitive values excluded?
- Are cardinality limits respected?

### Failure Modes

- Logs without context.
- Metrics without action.
- High-cardinality labels.
- Alerts without runbooks.
- Missing traces across service boundaries.

## 8. Privacy and Security

### Applies To

- APIs.
- Data.
- Logs.
- Events.
- AI systems.
- Integrations.

### Questions

- Is sensitive data involved?
- Is data minimized?
- Is data masked in logs and errors?
- Is authorization object-level?
- Are secrets separated from config?
- Are external providers receiving sensitive data?

### Failure Modes

- PII in logs.
- Secrets in prompts or traces.
- Missing object-level authorization.
- Over-broad data access.
- Data sent to third parties without policy review.

## 9. Testing

### Applies To

- All backend changes.

### Questions

- What behavior must not regress?
- Which invariants need tests?
- Are integration points tested?
- Are failure modes tested?
- Are migrations tested?
- Is telemetry tested?

### Failure Modes

- Happy-path-only tests.
- Over-mocked tests.
- No contract tests.
- No migration tests.
- No resilience tests.
- No observability verification.
