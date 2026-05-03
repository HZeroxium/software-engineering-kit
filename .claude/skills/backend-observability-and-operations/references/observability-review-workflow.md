---
purpose: Procedural 10-step workflow for reviewing or designing backend observability, with entry/exit criteria and skip conditions per step
load-when: Executing a full observability review or designing observability for a new backend feature
tier: domain
see-also:
  - release-and-rollback-readiness.md
  - runtime-configuration.md
  - java-observability-patterns.md
---

# Observability Review Workflow

## Entry Criteria

- User request or feature description is available.
- At least partial understanding of: what the service does and what failure looks like.

---

## Steps

### 1. Identify user-visible behavior and operational risk

- What user-facing operations does this change affect?
- What does "broken" look like from the user's perspective?
- What is the blast radius of a failure (one user, one tenant, all traffic)?
- **Skip:** only if scope is internal-only with no user-visible impact.

### 2. Determine what must be detected, diagnosed, and recovered

- Which failure modes are HIGH risk (data loss, full unavailability)?
- Which are LOW risk (degraded performance, retryable errors)?
- Map each failure mode: failure → detection signal → diagnosis path → mitigation action.
- **Skip:** only if a prior observability plan already covers this component with no new failure modes.

### 3. Review logging needs and sensitive-data constraints

- Which events are important enough to log? (state transitions, outcomes, errors, security events)
- Does any proposed log field risk sensitive data exposure (PII, tokens, raw payloads, large bodies)?
- Use `checklists/logging-checklist.md` as the quality gate.
- Use `references/structured-logging.md` for field selection guidance.

### 4. Review metrics needs, units, labels, and cardinality

- What aggregate trends must be monitorable? (request rate, error rate, latency, saturation, backlog)
- Are all proposed metric labels bounded (not user ID, request ID, email, or free-form strings)?
- Use `checklists/metrics-checklist.md` as the quality gate.
- Use `references/metrics-design-and-cardinality.md` for label rules and review questions.
- **Skip:** if no new user-visible operations are added (pure internal refactor, no new code paths).

### 5. Review tracing and context propagation (if relevant)

- Is this a multi-service or async workflow where a request crosses boundaries?
- Are correlation IDs propagated across service calls and async handoffs?
- Use `checklists/tracing-checklist.md` as the quality gate.
- Use `references/tracing-and-context-propagation.md` for boundary identification.
- **Skip:** if purely synchronous single-service change with existing trace instrumentation coverage.

### 6. Review alerts and runbooks for actionable user impact

- Are proposed alerts symptom-based and tied to user-visible failure?
- Does each alert have a linked runbook draft?
- Use `references/alerting-and-runbooks.md` for quality principles.
- Use `references/slo-and-error-budgets.md` to validate that alert thresholds are principled.
- Use `templates/alert-and-runbook-review.md` for output format.
- **Skip:** if no new failure modes are introduced and existing alerts cover the changed behavior.

### 7. Review health checks, runtime config, and release/rollback readiness

- Does the change affect liveness or readiness behavior, or introduce a dependency that could drain instances?
- Does it add new config that must be validated at startup and documented for each environment?
- Is rollback safe after the change? Is a feature flag or kill switch needed?
- Load `references/health-checks.md`, `references/runtime-configuration.md`, and `references/release-and-rollback-readiness.md` as needed.
- **Skip individual sub-topics** if the change does not touch health checks, config, or release behavior.

### 8. Identify sensitive data and cardinality risks — mandatory, no skip

- Cross-check ALL proposed telemetry (logs, metrics, traces, alerts) for: PII, tokens, secrets, raw request/response payloads, large bodies.
- Cross-check ALL proposed metric labels for unbounded dimensions.
- If any risk is found, apply the minimal-information principle: log/trace/measure only safe identifiers, not raw values.

### 9. Define validation plan

- How will each telemetry signal be verified? (unit test, integration test, manual log review, CI metrics emission check)
- Which validations are not possible in this context, and why?
- State explicitly what was not validated.

### 10. Summarize gap analysis and residual risks

- Produce a structured observability gap analysis using `templates/observability-plan.md`.
- List: confirmed signals | still-missing signals | deferred (with reason) | blocked (with reason).
- State residual risks explicitly — do not silently omit gaps.

---

## Exit / Quality Bar

- All HIGH-risk failure modes have at least one detection signal.
- No sensitive data in any proposed telemetry.
- No unbounded metric label proposed without explicit justification.
- Validation plan is explicit, including what was not run.
- Gaps are named and categorized, not silently skipped.
