---
name: backend-observability-and-operations
description: Framework-agnostic backend Skill for logs, metrics, traces, dashboards, alerts, runbooks, health checks, runtime config, release/rollback readiness, production diagnostics, and operational readiness.
---

# Backend Observability and Operations

## Activation Criteria

Use this Skill when the task involves any of:

- Adding or reviewing logs, metrics, or traces for a backend change.
- Designing or reviewing alerts and runbooks.
- Reviewing health checks, runtime configuration, or feature flags.
- Assessing release or rollback readiness from an operations perspective.
- Production diagnostics — interpreting missing telemetry or identifying observability gaps.
- Operational readiness review before a release.

Do not use this Skill for:

- DevOps platform engineering (CI/CD pipelines, infra provisioning, Kubernetes cluster setup).
- Pure performance profiling without observability planning.
- Frontend or client-side observability.

## Purpose

Analyze backend observability and runtime operational readiness.

This Skill covers:

- Logs.
- Metrics.
- Traces.
- Dashboards.
- Alerts.
- Runbooks.
- Health checks.
- Runtime configuration.
- Release and rollback readiness.
- Production diagnostics.

It focuses on backend operations readiness, not full DevOps platform engineering.

## Required Inputs

Use available context first. Ask only when missing context materially affects safety or scope.

**Required:**
- Description of the backend change or feature being reviewed.

**Strongly recommended:**
- Relevant source files (service, use-case, job, or integration being changed).
- Existing telemetry conventions discovered from repo (metric names, log field patterns, tracing library usage).

**Useful when available:**
- Current logs, metrics dashboard queries, or alert definitions.
- Architecture context (sync vs async, multi-service, messaging).
- Known sensitive-data fields or compliance constraints.
- Release strategy (canary, feature flag, blue/green).
- Stack and observability tooling (do not assume — discover from repo).

## Non-Goals

Do not:

- Assume Prometheus, Grafana, OpenTelemetry, ELK, Datadog, Kubernetes, or any specific tool.
- Invent metric names, log fields, tracing APIs, alert syntax, dashboard queries, or command syntax.
- Add high-cardinality labels without justification.
- Log secrets, PII, tokens, raw payloads, or sensitive data.
- Treat telemetry volume as free.

## Workflow

For full procedural detail with skip conditions and quality bar per step, load `references/observability-review-workflow.md`.

1. **Identify user-visible behavior and operational risk.**
   - What does "broken" look like from the user's perspective?
   - What is the blast radius of a failure?

2. **Determine what must be detected, diagnosed, and recovered.**
   - Map failure mode → detection signal → diagnosis path → mitigation action.

3. **Review logging needs and sensitive-data constraints.**
   - Use `checklists/logging-checklist.md` as the quality gate.

4. **Review metrics needs, units, labels, and cardinality.**
   - Use `checklists/metrics-checklist.md` and `references/metrics-design-and-cardinality.md`.

5. **Review tracing and context propagation if relevant.**
   - Use `checklists/tracing-checklist.md` and `references/tracing-and-context-propagation.md`.

6. **Review alerts and runbooks for actionable user impact.**
   - Use `references/alerting-and-runbooks.md` and `references/slo-and-error-budgets.md`.

7. **Review health checks, runtime config, and release/rollback readiness.**
   - Load scenario references as needed.

8. **Identify sensitive data and cardinality risks — mandatory, no skip.**

9. **Define validation plan.**

10. **Summarize gap analysis and residual risks.**
    - Use `templates/observability-plan.md` for output.

## Expected Outputs

Output type: **mixed** — this Skill produces different outputs depending on scope:

- **analysis** — gap analysis phase: identifies missing signals, failure modes without coverage, sensitive data risks. Use `templates/observability-plan.md`.
- **plan** — design phase: logging plan, metrics plan, tracing plan, alert/runbook notes, health/config/runtime concerns, release/rollback readiness. Use `templates/observability-plan.md`.
- **report** — review phase: findings ordered by severity (Blocking / Important / Optional) with evidence and minimal fix. Use `templates/logging-review.md`, `templates/metrics-review.md`, `templates/tracing-review.md`, `templates/alert-and-runbook-review.md`.
- **checklist** — readiness gate: go/no-go before release. Use `templates/operational-readiness-review.md` and `checklists/operations-readiness-checklist.md`.

For simple or narrow scope, compress into a single structured response while preserving gap analysis, sensitive data risk, and validation plan.

## Safety Boundaries

Ask for clarification or repo evidence when:

- Existing telemetry conventions are unknown.
- Metrics labels may create high cardinality.
- Logs may contain sensitive data.
- Health checks affect traffic routing.
- Runtime config or release behavior affects production.

## Supporting Files

Load only when useful. Start with `references/reference-index.md` when the task is broad or multiple references may apply.

| File | Purpose | Load when |
| --- | --- | --- |
| `references/reference-index.md` | Semantic navigation graph for all references with tier, purpose, and load-when for each | Starting a broad review or unsure which reference to load first |
| `references/metrics-logs-traces.md` | Three signal types vocabulary and 4 operator questions | Starting any observability review — load first |
| `references/observability-review-workflow.md` | 10-step procedural workflow with skip conditions and quality bar | Executing a full observability review |
| `references/structured-logging.md` | Structured log fields, sensitive-data rules, and logging smells | Reviewing or designing logging |
| `references/metrics-design-and-cardinality.md` | Metric types, label rules, cardinality risk review | Reviewing or designing metrics |
| `references/tracing-and-context-propagation.md` | Trace boundaries, context propagation, and failure modes | Reviewing or designing distributed tracing |
| `references/alerting-and-runbooks.md` | Alert quality principles and runbook structure guide | Reviewing alerts or drafting runbooks |
| `references/slo-and-error-budgets.md` | SLI/SLO/error budget concepts and burn-rate alert design | Designing alerts or reviewing observability maturity |
| `references/health-checks.md` | Liveness/readiness check types and failure modes | Change affects health check or traffic routing behavior |
| `references/release-and-rollback-readiness.md` | Backward-compatibility, feature flag, and rollback failure modes | Release or rollback concerns are present |
| `references/runtime-configuration.md` | Feature flags, kill switches, config validation, secrets separation | Change adds or modifies runtime configuration |
| `references/java-observability-patterns.md` | Java-specific illustrative patterns for logging/metrics/tracing | Working in a Java codebase |
| `templates/observability-plan.md` | Observability plan template | Producing a structured observability plan |
| `templates/logging-review.md` | Logging review template | Reviewing logging for a specific feature or module |
| `templates/metrics-review.md` | Metrics review template | Reviewing metric design and cardinality |
| `templates/tracing-review.md` | Tracing review template | Reviewing tracing boundaries and propagation |
| `templates/alert-and-runbook-review.md` | Alert and runbook review template | Reviewing or drafting alerts and runbooks |
| `templates/operational-readiness-review.md` | Operational readiness review template | Release gate review |
| `checklists/observability-checklist.md` | Scope-level gate: are all signals planned? | Confirming observability coverage at feature/release level |
| `checklists/logging-checklist.md` | Logging signal quality gate | Reviewing logging in depth |
| `checklists/metrics-checklist.md` | Metrics signal quality gate | Reviewing metrics in depth |
| `checklists/tracing-checklist.md` | Tracing signal quality gate | Reviewing tracing in depth |
| `checklists/runbook-checklist.md` | Runbook completeness gate | Reviewing a runbook |
| `checklists/operations-readiness-checklist.md` | Operations release gate | Pre-release operational readiness |
| `examples/java-logging-metrics-tracing-review-example.md` | Worked example: Java async job observability review | Calibrating review depth or output format |
