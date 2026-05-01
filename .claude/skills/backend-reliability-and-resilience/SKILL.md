---
name: backend-reliability-and-resilience
description: Framework-agnostic backend Skill for reliability under dependency failure, traffic, partial outages, incidents, SLOs/SLIs, error budgets, graceful degradation, fault tolerance, availability, disaster recovery, and resilience testing.
---

# Backend Reliability and Resilience

Use this Skill when a backend task involves timeout, retry, idempotency, dependency degradation, availability, incident response, fallback behavior, graceful degradation, disaster recovery, or resilience testing.

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

## Expected Output

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

## Safety Boundaries

Ask for clarification or repo evidence when:

- Production SLOs are unknown.
- Dependencies and failure behavior are unclear.
- Retries may increase outage impact.
- Fallback behavior affects user-visible correctness.
- Incident or disaster recovery processes are not documented.
