---
name: backend-observability-and-operations
description: Framework-agnostic backend Skill for logs, metrics, traces, dashboards, alerts, runbooks, health checks, runtime config, release/rollback readiness, production diagnostics, and operational readiness.
---

# Backend Observability and Operations

Use this Skill when adding or changing backend behavior that needs logging, metrics, traces, alerts, health checks, configuration, runtime controls, runbooks, release safety, rollback readiness, or production diagnostics.

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

## Non-Goals

Do not:

- Assume Prometheus, Grafana, OpenTelemetry, ELK, Datadog, Kubernetes, or any specific tool.
- Invent metric names, log fields, tracing APIs, alert syntax, dashboard queries, or command syntax.
- Add high-cardinality labels without justification.
- Log secrets, PII, tokens, raw payloads, or sensitive data.
- Treat telemetry volume as free.

## Workflow

1. Identify user-visible behavior and operational risk.
2. Determine what must be detected, diagnosed, and recovered.
3. Review logging needs and sensitive-data constraints.
4. Review metrics needs, units, labels, and cardinality.
5. Review tracing and context propagation if relevant.
6. Review alerts and runbooks for actionable user impact.
7. Review health checks, runtime config, and release/rollback readiness.
8. Define validation plan.
9. Separate confirmed facts, assumptions, hypotheses, and unknowns.

## Expected Output

Return:

- Observability gap analysis.
- Logging plan.
- Metrics plan.
- Tracing plan.
- Alert/runbook notes.
- Health/config/runtime concerns.
- Release/rollback readiness.
- Sensitive data and cardinality risks.
- Validation plan.

## Safety Boundaries

Ask for clarification or repo evidence when:

- Existing telemetry conventions are unknown.
- Metrics labels may create high cardinality.
- Logs may contain sensitive data.
- Health checks affect traffic routing.
- Runtime config or release behavior affects production.
