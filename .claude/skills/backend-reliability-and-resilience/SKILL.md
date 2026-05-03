---
name: backend-reliability-and-resilience
description: Framework-agnostic backend Skill for reliability under dependency failure, traffic, partial outages, incidents, SLOs/SLIs, error budgets, graceful degradation, fault tolerance, availability, disaster recovery, and resilience testing.
---

# Backend Reliability and Resilience

Use this Skill when a backend task involves timeout, retry, idempotency, dependency degradation, availability, incident response, fallback behavior, graceful degradation, disaster recovery, or resilience testing.

## Required Inputs

- Feature or service description.
- Known dependencies (sync, async, or external).
- Existing SLO/SLI targets (or "unknown").
- Observed or anticipated failure modes.
- Operational context: alerts, runbooks, deployment model.

## Purpose

Analyze backend reliability and resilience under dependency failure, traffic, partial outages, and operational incidents.

This Skill covers:

- User-visible reliability targets.
- SLOs, SLIs, and error budgets.
- Critical dependency mapping.
- Graceful degradation.
- Fault tolerance.
- Timeout, retry, circuit breaker, and bulkhead implications.
- Availability and failover.
- Disaster recovery, RPO, and RTO.
- Incident readiness.
- Resilience testing.

## Non-Goals

Do not:

- Assume specific observability, deployment, service mesh, cloud, or orchestration tools.
- Treat internal symptoms as equivalent to user impact.
- Recommend retries without overload and idempotency analysis.
- Claim resilience without tests or operational evidence.
- Ignore manual incident response and rollback needs.

## Workflow

1. Define user-visible reliability target.
2. Identify critical user journeys and dependencies.
3. Map dependency failure modes.
4. Analyze fallback and graceful degradation behavior.
5. Analyze timeout, retry, circuit breaker, and bulkhead implications.
6. Identify SLO/SLI and error-budget considerations.
7. Review disaster recovery, RPO/RTO, and incident readiness if relevant.
8. Define resilience tests and operational validation.
9. Separate confirmed facts, assumptions, hypotheses, and unknowns.

## Expected Outputs

Output type: **mixed** — combines reliability analysis, dependency failure map, resilience design notes, test plan, and open questions.

Return:

- User-visible reliability target.
- Critical dependency map.
- Failure modes.
- Fallback/degradation behavior.
- Retry/circuit breaker/bulkhead implications.
- SLO/SLI considerations.
- Resilience tests.
- Incident readiness notes.
- Open questions and required evidence.

## Validation

Test this Skill with:

- Direct: `/backend-reliability-and-resilience`
- Auto-activation prompt: "How should we handle timeouts calling the payment service?"
- Auto-activation prompt: "Our SLO is 99.9% but we don't have a circuit breaker — what's the risk?"
- Non-activation boundary: "How do I write a Spring Boot controller?" (should not activate)

## Supporting Files

| Folder | File | Use when |
| ------ | ---- | -------- |
| `references/` | `reference-index.md` | Quick overview of reference graph before loading individual files |
| `references/` | `reliability-availability-resilience.md` | Core vocabulary needed — load first |
| `references/` | `timeout-retry-circuit-breaker-bulkhead.md` | Timeout, retry, circuit breaker, or bulkhead review |
| `references/` | `slo-sli-error-budget.md` | SLO/SLI definition or error budget analysis |
| `references/` | `graceful-degradation.md` | Fallback or partial-availability design |
| `references/` | `resilience-testing.md` | Resilience test design |
| `references/` | `load-shedding-and-backpressure.md` | Overload, queue saturation, or traffic spike risk |
| `references/` | `cascading-failure-patterns.md` | Cascading failure, retry storm, or thundering herd risk |
| `references/` | `disaster-recovery-rpo-rto.md` | DR, RPO, RTO, or multi-region failover in scope |
| `references/` | `incident-response-and-postmortem.md` | Incident readiness or postmortem review |
| `references/` | `java-reliability-examples.md` | Java code examples explicitly requested |
| `checklists/` | `reliability-checklist.md` | Quick reliability gate check |
| `checklists/` | `dependency-failure-checklist.md` | Per-dependency failure mode review |
| `checklists/` | `incident-readiness-checklist.md` | Incident readiness review |
| `checklists/` | `resilience-testing-checklist.md` | Resilience test planning |
| `templates/` | `reliability-review.md` | Full reliability review output |
| `templates/` | `resilience-design-plan.md` | Resilience design for a new feature |
| `templates/` | `dependency-failure-analysis.md` | Per-dependency analysis |
| `templates/` | `slo-sli-analysis.md` | SLO/SLI definition and gap analysis |
| `templates/` | `incident-readiness-review.md` | Incident readiness output |
| `examples/` | `backend-timeout-retry-review-example.md` | Timeout/retry review scenario |
| `examples/` | `slo-breach-incident-triage-example.md` | SLO breach and incident triage scenario |

## Safety Boundaries

Ask for clarification or repo evidence when:

- Production SLOs are unknown.
- Dependencies and failure behavior are unclear.
- Retries may increase outage impact.
- Fallback behavior affects user-visible correctness.
- Incident or disaster recovery processes are not documented.
