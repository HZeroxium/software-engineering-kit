---
name: backend-development-core
description: Backend development router and scope model. Use for broad, unclear, or cross-cutting backend tasks to classify scope, identify risks, select specialized backend Skills, and produce a high-level framework-agnostic analysis before implementation.
---

# Backend Development Core

Use this Skill when a backend request is broad, vague, multi-scope, high-risk, or needs routing to a more specialized backend Skill.

This Skill is a router and reasoning aid. It is not a do-everything implementation Skill.

## Primary Purpose

Classify backend tasks into the right backend scope, identify risks and assumptions, select the appropriate specialized backend Skill, and produce a concise high-level analysis before deeper design, implementation, review, or debugging.

## Activation Criteria

Use this Skill when the user asks about:

- Broad backend development topics.
- Backend architecture or system design.
- Backend feature design or implementation strategy.
- Backend task scope classification.
- Backend risk triage.
- Backend review triage.
- Backend Skill selection.
- Vague requests such as “design this backend feature”, “how should I implement this?”, “review this backend change”, “what scope is this?”, or “which backend concerns matter here?”

Use this Skill before specialized backend Skills when task boundaries are unclear.

## Non-Goals

Do not:

- Implement code directly.
- Perform full code review unless the user asks only for triage.
- Duplicate specialized backend Skill content.
- Assume Spring, FastAPI, NestJS, cloud provider, vendor platform, database, queue, framework, or internal library behavior without repo evidence.
- Invent APIs, commands, framework behavior, internal library behavior, or organization-specific conventions.
- Recommend broad rewrites before classifying scope and risk.

## Required Inputs

- Backend request or task description (required).
- Repository context such as module structure, existing API contracts, domain model, or technology stack (optional; request when task risk is High or Critical).
- Technology constraints confirmed from the repo (optional; do not assume framework, cloud provider, or internal library behavior).

## Compressed Backend Scope Model

Use this 9-scope model for active routing:

1. **backend-domain-and-api-design**
   - Domain modeling, business capabilities, bounded contexts, API/interface design, business logic correctness, contracts, versioning, error models, idempotency.

2. **backend-application-architecture**
   - Use-case orchestration, application services, transaction boundaries, workflows/state machines, modularity, dependency architecture, Clean/Hexagonal/Layered architecture, SOLID, design patterns.

3. **backend-data-and-persistence**
   - Data ownership, schema design, transactions, consistency, indexing, query patterns, caching, migrations, data lifecycle, multi-tenancy.

4. **backend-security-and-trust**
   - AuthN/AuthZ, object-level access control, tenant isolation, secrets, input/output security, audit logging, threat modeling, abuse prevention.

5. **backend-integration-and-distributed-communication**
   - Sync APIs, RPC, async messaging, event contracts, retries/timeouts, circuit breakers, bulkheads, backpressure, idempotent consumers, outbox/inbox.

6. **backend-reliability-and-resilience**
   - SLOs/SLIs, graceful degradation, fault tolerance, availability, failover, disaster recovery, incident response, resilience testing.

7. **backend-performance-and-scalability**
   - Latency, throughput, p95/p99, capacity, resource efficiency, database performance, caching, concurrency, load testing, cost-performance trade-offs.

8. **backend-observability-and-operations**
   - Metrics, logs, traces, dashboards, alerts, runbooks, CI/CD, release strategy, health checks, configuration, runtime controls.

9. **backend-ai-governance-and-quality**
   - Testing/verification, governance, privacy, compliance, Applied AI backend engineering, RAG/agents/model integration, AI evaluation, AI safety, AI observability.

For deeper analysis, use `references/backend-15-scope-model.md`.

## Routing Workflow

1. Restate the backend task in one sentence.
2. Classify the task type:
   - Project onboarding
   - Feature design
   - Feature implementation planning
   - Review triage
   - Domain/API design
   - Architecture analysis
   - Data/persistence analysis
   - Security/trust analysis
   - Integration/distributed systems analysis
   - Reliability/resilience analysis
   - Performance/scalability analysis
   - Observability/operations analysis
   - AI/governance/quality analysis
3. Select primary and secondary backend scopes.
4. Identify cross-cutting concerns:
   - Error handling
   - Idempotency
   - Configuration
   - Multi-tenancy
   - Cost
   - Governance
   - Observability
   - Privacy/security
   - Testing
5. Identify assumptions, unknowns, and required context.
6. Identify risk level:
   - Low
   - Medium
   - High
   - Critical
7. Recommend the next specialized Skill or next safe action.
8. Produce a handoff prompt if another Skill should continue.

## Expected Outputs

Output type: **mixed** (classification + analysis + recommendation + handoff prompt)

Return:

- Backend task classification.
- Primary and secondary backend scopes.
- Recommended specialized Skill(s).
- Key risks and assumptions.
- Context needed.
- Suggested next action.
- Handoff prompt to the selected Skill.

Use these templates when useful:

- `templates/backend-task-classification.md`
- `templates/backend-scope-selection.md`
- `templates/backend-analysis-summary.md`
- `templates/backend-risk-register.md`
- `templates/backend-skill-handoff.md`

## Decision Rules

Prefer:

- Project onboarding before implementation in unfamiliar repositories.
- Domain/API design before data modeling when business behavior is unclear.
- Security/trust analysis before implementation when identity, permissions, tenant isolation, secrets, or sensitive data are involved.
- Data/persistence analysis before implementation when schema, transactions, migrations, consistency, or query performance are involved.
- Integration/distributed communication analysis before implementation when service boundaries, retries, messaging, events, or external APIs are involved.
- Reliability/performance/observability analysis before production rollout.
- AI/governance/quality analysis when model calls, RAG, agents, prompts, evaluations, privacy, or AI safety are involved.

## Safety Boundaries

Before recommending implementation, check for:

- Auth/security impact.
- Object-level authorization.
- Tenant isolation.
- Secrets or credentials.
- Production configuration.
- Migrations and data mutation.
- CI/CD and infrastructure.
- External system writes.
- Dependency upgrades.
- Generated code.
- Internal libraries with unclear behavior.
- Missing validation commands.
- Missing tests.
- Missing observability.

## Final Response Shape

Use `templates/backend-task-classification.md` for output format.

## Supporting Files

| File | Purpose | Load when |
|------|---------|-----------|
| `references/reference-index.md` | Navigation map for all reference files with tiers and load conditions | Load first to navigate the reference graph without loading all files |
| `references/framework-agnostic-backend-principles.md` | Core principles for framework-agnostic analysis | Any broad backend task |
| `references/backend-9-skill-library-map.md` | Deep routing map with inputs and outputs per scope | Primary scope selection |
| `references/backend-15-scope-model.md` | Full 15-scope taxonomy for deep analysis | When 9-scope routing is insufficient |
| `references/backend-cross-cutting-concerns.md` | Cross-cutting concerns across all scopes | When multiple scopes overlap |
| `references/backend-failure-modes.md` | Failure modes per scope for risk triage | When identifying specific failure risks |
| `references/backend-quality-attributes.md` | Quality attribute trade-off analysis | When evaluating backend designs |
| `checklists/backend-task-triage-checklist.md` | Task understanding and scope selection checklist | Starting any backend task |
| `checklists/backend-skill-selection-checklist.md` | Decision checklist for selecting the right specialized Skill | After primary scope is identified |
| `checklists/backend-risk-triage-checklist.md` | Risk triage checklist across all backend risk categories | When risk level is Medium or above |
| `templates/backend-task-classification.md` | Output format for backend task classification | Producing the classification output |
| `templates/backend-scope-selection.md` | Output format for scope selection reasoning | When scope is contested or multi-scope |
| `templates/backend-analysis-summary.md` | Output format for backend analysis summary | When a concise analysis summary is needed |
| `templates/backend-risk-register.md` | Output format for the risk register | When risk level is High or Critical |
| `templates/backend-skill-handoff.md` | Handoff prompt to the selected specialized Skill | Always — at end of routing workflow |
| `examples/backend-task-classification-example.md` | Worked example: payment order (integration scope) | Validating output format and routing |
| `examples/backend-api-design-routing-example.md` | Worked example: subscription plan update (domain/API scope) | Validating routing for domain/API tasks |
| `examples/backend-security-triage-example.md` | Worked example: admin profile API (security scope, Critical risk) | Validating routing for security-sensitive tasks |
