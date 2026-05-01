# Backend Skill Selection Checklist

## First Question

Is the repository unfamiliar?

- [ ] Yes → Recommend project onboarding first.
- [ ] No → Continue scope routing.

## Select Primary Skill

### backend-domain-and-api-design

Use when:

- [ ] Business rules are unclear.
- [ ] API contract is central.
- [ ] Error model is central.
- [ ] Idempotency is central.
- [ ] Versioning or compatibility is central.

### backend-application-architecture

Use when:

- [ ] Use-case orchestration is central.
- [ ] Transaction boundary is unclear.
- [ ] Workflow/state machine is involved.
- [ ] Dependency/module architecture is central.
- [ ] Design patterns or layering are central.

### backend-data-and-persistence

Use when:

- [ ] Data model/schema is central.
- [ ] Transactions/consistency are central.
- [ ] Query/index performance is central.
- [ ] Migration is involved.
- [ ] Cache correctness is involved.
- [ ] Multi-tenancy data isolation is involved.

### backend-security-and-trust

Use when:

- [ ] AuthN/AuthZ is involved.
- [ ] Object-level authorization is involved.
- [ ] Tenant isolation is involved.
- [ ] Secrets or sensitive data are involved.
- [ ] Audit logging or threat modeling is needed.

### backend-integration-and-distributed-communication

Use when:

- [ ] Service-to-service communication is involved.
- [ ] RPC/API integration is involved.
- [ ] Messaging/events are involved.
- [ ] Retry/timeout/circuit breaker behavior is involved.
- [ ] Idempotent consumers or outbox/inbox are involved.

### backend-reliability-and-resilience

Use when:

- [ ] Availability is central.
- [ ] Dependency failure behavior is central.
- [ ] SLOs/SLIs are involved.
- [ ] Graceful degradation is needed.
- [ ] Disaster recovery or incident readiness is involved.

### backend-performance-and-scalability

Use when:

- [ ] Latency or throughput is central.
- [ ] p95/p99 is central.
- [ ] Database performance is central.
- [ ] Concurrency or capacity is central.
- [ ] Load testing or resource efficiency is needed.

### backend-observability-and-operations

Use when:

- [ ] Metrics/logs/traces are central.
- [ ] Dashboards/alerts/runbooks are central.
- [ ] CI/CD or release is central.
- [ ] Health checks/config/runtime controls are central.
- [ ] Operational debugging is central.

### backend-ai-governance-and-quality

Use when:

- [ ] AI model calls are involved.
- [ ] RAG/agents/prompting are involved.
- [ ] AI evaluation is needed.
- [ ] AI observability or AI safety is involved.
- [ ] Testing, governance, privacy, or compliance is the main concern.

## Handoff Required?

- [ ] The selected Skill needs more context.
- [ ] The selected Skill should receive risk constraints.
- [ ] The selected Skill should receive assumptions to avoid.
- [ ] The selected Skill should receive expected output format.

If any are checked, produce a handoff prompt.
