# Backend 9-Skill Library Map

## Purpose

This file maps broad backend development requests to specialized backend Skills. The active `SKILL.md` should use this compressed model for routing.

## 1. backend-domain-and-api-design

### Covers

- Domain modeling.
- Business capabilities.
- Bounded contexts.
- API/interface design.
- Business logic correctness.
- Contracts.
- Versioning.
- Error models.
- Idempotency.

### Use When

- The user asks how to design a feature contract.
- Business concepts or workflows are unclear.
- API shape is unclear.
- Errors, versioning, compatibility, or idempotency matter.
- The main risk is correctness at the domain/API boundary.

### Common Inputs

- Feature description.
- Business rules.
- Existing API examples.
- Domain model.
- API schema.
- Error contract.
- Client requirements.

### Expected Outputs

- Domain model.
- API contract recommendation.
- Error model.
- Compatibility and versioning notes.
- Idempotency strategy.
- Open business questions.

---

## 2. backend-application-architecture

### Covers

- Use-case orchestration.
- Application services.
- Transaction boundaries.
- Workflows/state machines.
- Modularity.
- Dependency architecture.
- Clean/Hexagonal/Layered architecture.
- SOLID.
- Design patterns.

### Use When

- The user asks where logic should live.
- A feature involves multiple steps, external calls, or side effects.
- Transaction boundaries are unclear.
- The codebase structure is hard to reason about.
- Dependency direction or testability is a concern.

### Common Inputs

- Use case.
- Current package/module structure.
- Existing service classes.
- Transaction behavior.
- External dependencies.
- Validation rules.

### Expected Outputs

- Use-case flow.
- Layer/module responsibility split.
- Transaction boundary.
- Dependency design.
- Failure handling.
- Minimal implementation plan.

---

## 3. backend-data-and-persistence

### Covers

- Data ownership.
- Schema design.
- Transactions.
- Consistency.
- Indexing.
- Query patterns.
- Caching.
- Migrations.
- Data lifecycle.
- Multi-tenancy.

### Use When

- The task changes stored data.
- Queries are slow or complex.
- Migrations are needed.
- Cache correctness matters.
- Multi-tenant data isolation matters.
- Consistency and transaction guarantees are unclear.

### Common Inputs

- Entity/schema definitions.
- Query patterns.
- Migration files.
- Transaction requirements.
- Volume/cardinality assumptions.
- Cache usage.

### Expected Outputs

- Data model recommendation.
- Transaction and consistency plan.
- Index/query advice.
- Migration safety plan.
- Cache strategy.
- Data lifecycle risks.

---

## 4. backend-security-and-trust

### Covers

- Authentication.
- Authorization.
- Object-level access control.
- Tenant isolation.
- Secrets.
- Input/output security.
- Audit logging.
- Threat modeling.
- Abuse prevention.

### Use When

- The task touches identity, permissions, tenants, secrets, PII, admin actions, or trust boundaries.
- Object ownership checks are needed.
- Sensitive data may be logged, returned, stored, or sent externally.
- Abuse, rate limit, or privilege escalation risks exist.

### Common Inputs

- Auth model.
- Roles/permissions.
- Resource ownership rules.
- API contract.
- Data sensitivity.
- Logs/events.
- Threat assumptions.

### Expected Outputs

- Security boundary analysis.
- Authorization plan.
- Object-level access control checklist.
- Secret/sensitive data handling.
- Audit logging plan.
- Threat model summary.

---

## 5. backend-integration-and-distributed-communication

### Covers

- Sync APIs.
- RPC.
- Async messaging.
- Event contracts.
- Retries/timeouts.
- Circuit breakers.
- Bulkheads.
- Backpressure.
- Idempotent consumers.
- Outbox/inbox.

### Use When

- The task crosses service boundaries.
- External APIs or third-party providers are involved.
- Queues, events, RPC, or webhooks are involved.
- Retry, timeout, duplicate delivery, or partial failure matters.
- Event schema compatibility matters.

### Common Inputs

- Service interaction diagram.
- API/event schema.
- Retry/timeout requirements.
- Delivery semantics.
- Failure cases.
- Provider limits.

### Expected Outputs

- Communication style recommendation.
- Contract strategy.
- Retry/timeout policy.
- Idempotency and duplicate handling.
- Outbox/inbox recommendation.
- Failure mode analysis.

---

## 6. backend-reliability-and-resilience

### Covers

- SLOs/SLIs.
- Graceful degradation.
- Fault tolerance.
- Availability.
- Failover.
- Disaster recovery.
- Incident response.
- Resilience testing.

### Use When

- The task affects production reliability.
- The system must tolerate dependency failure.
- SLOs, uptime, or recovery targets matter.
- Fallback and degradation behavior is needed.
- Incident readiness is unclear.

### Common Inputs

- Critical user journeys.
- Dependency list.
- Current failure behavior.
- SLO/SLI targets.
- Alerts/runbooks.
- DR assumptions.

### Expected Outputs

- Reliability target clarification.
- Failure mode matrix.
- Degradation/fallback strategy.
- Recovery plan.
- Resilience tests.
- Incident readiness gaps.

---

## 7. backend-performance-and-scalability

### Covers

- Latency.
- Throughput.
- p95/p99.
- Capacity.
- Resource efficiency.
- Database performance.
- Caching.
- Concurrency.
- Load testing.
- Cost-performance trade-offs.

### Use When

- The user asks about slow code, high load, high cardinality, resource usage, scaling, or cost.
- Queries or external calls may dominate latency.
- Concurrency or connection pools matter.
- Load testing or capacity planning is needed.

### Common Inputs

- Metrics.
- Traces.
- Logs.
- Query plans.
- Load assumptions.
- Resource usage.
- Architecture diagram.

### Expected Outputs

- Bottleneck hypothesis.
- Measurement plan.
- Optimization options.
- Trade-offs.
- Load test plan.
- Regression monitoring plan.

---

## 8. backend-observability-and-operations

### Covers

- Metrics.
- Logs.
- Traces.
- Dashboards.
- Alerts.
- Runbooks.
- CI/CD.
- Release strategy.
- Health checks.
- Configuration.
- Runtime controls.

### Use When

- The task concerns production visibility or operations.
- The user asks for metrics, dashboards, logs, traces, alerts, or runbooks.
- CI/CD, release, rollback, config, or health checks are involved.
- Runtime debugging or operational readiness is needed.

### Common Inputs

- Existing telemetry.
- Prometheus/Grafana queries.
- Logs/traces.
- CI/CD pipeline.
- Deployment config.
- Health check behavior.
- Incident symptoms.

### Expected Outputs

- Observability coverage analysis.
- Metrics/logs/traces design.
- Dashboard/alert recommendations.
- Release/rollback notes.
- Runbook outline.
- Operational risks.

---

## 9. backend-ai-governance-and-quality

### Covers

- Testing and verification.
- Governance.
- Privacy.
- Compliance.
- Applied AI backend engineering.
- RAG/agents/model integration.
- AI evaluation.
- AI safety.
- AI observability.

### Use When

- The task involves AI model calls, prompts, RAG, agents, tool calling, AI evaluation, AI observability, or AI governance.
- Testing strategy is the primary concern.
- Privacy/compliance/risk review is central.
- The output quality of AI features must be measured and monitored.

### Common Inputs

- AI use case.
- Prompt/context flow.
- Retrieval design.
- Model/provider config.
- Evaluation data.
- Privacy requirements.
- Tool permissions.
- Test strategy.

### Expected Outputs

- AI appropriateness analysis.
- Prompt/context/retrieval risk analysis.
- Evaluation plan.
- AI observability plan.
- Privacy/safety controls.
- Human approval boundaries.
