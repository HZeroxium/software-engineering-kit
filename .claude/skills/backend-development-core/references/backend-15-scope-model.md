---
purpose: Full 15-scope technology-neutral backend taxonomy with definitions, key concerns, typical questions, failure modes, and AI guidance per scope
load-when: 9-scope routing is insufficient or deeper scope analysis is needed for a specific area
tier: domain
see-also:
  - backend-failure-modes.md
  - backend-cross-cutting-concerns.md
---

# Backend 15-Scope Model

## Purpose

This reference preserves the full technology-neutral backend development taxonomy. Use it for deeper analysis after the active 9-scope routing model has selected the relevant area.

Backend development should be reasoned about as engineering scopes, not as a list of tools. Frameworks, databases, queues, cloud services, and AI APIs are implementation choices. The deeper concerns are domain boundaries, APIs, data, security, correctness, reliability, scalability, observability, operations, testing, governance, and AI quality.

## Scope Hierarchy

```text
Backend Development
├── 1. Domain & Business Capability Design
├── 2. API & Interface Design
├── 3. Application Architecture & Use-Case Orchestration
├── 4. Data Architecture & Persistence
├── 5. Security, Identity & Trust
├── 6. Validation, Correctness & Business Rule Enforcement
├── 7. Modularity, Dependency Architecture & Codebase Structure
├── 8. Integration & Distributed Communication
├── 9. Reliability, Resilience & Availability
├── 10. Performance, Scalability & Efficiency
├── 11. Observability, Monitoring & Alerting
├── 12. Delivery, Operations & Runtime Management
├── 13. Testing, Verification & Quality Engineering
├── 14. Governance, Privacy, Compliance & Risk
└── 15. Applied AI Backend Engineering
```

---

## 1. Domain & Business Capability Design

### Definition

Domain and business capability design is the discipline of understanding the business problem, modeling core concepts, and defining clear ownership boundaries around business capabilities.

### Key Concerns

- Domain modeling.
- Bounded contexts.
- Business capabilities.
- Aggregates.
- Domain events.
- Business invariants.
- Ubiquitous language.
- Ownership boundaries.

### Typical Questions

- What business problem does the backend solve?
- What are the core entities, value objects, and workflows?
- Which rules must always hold true?
- Where are the boundaries between capabilities?
- Which events represent important business facts?

### Common Failure Modes

- Starting from database tables instead of business capabilities.
- Mixing unrelated concepts in one module or service.
- Placing all business logic in controllers, handlers, or application services.
- Using vague names that do not match the business language.
- Creating “common” business modules with unclear ownership.

### AI Guidance

Ask the AI to identify concepts, invariants, boundaries, events, ownership, and misplaced business logic.

---

## 2. API & Interface Design

### Definition

API and interface design defines how backend capabilities are exposed to clients, services, integrations, and external systems.

### Key Concerns

- API style: REST, RPC, GraphQL, events, webhooks, streaming.
- Request/response contracts.
- Resource and command modeling.
- Error models.
- Versioning.
- Pagination.
- Filtering and sorting.
- Idempotency.
- Rate limiting and quotas.
- Documentation and examples.

### Typical Questions

- Is the API resource-oriented, action-oriented, workflow-oriented, or event-oriented?
- Is the contract backward compatible?
- What are the possible errors?
- Which errors are retryable?
- Does the API require idempotency?
- Are internal implementation details leaking through the API?

### Common Failure Modes

- Inconsistent errors.
- CRUD-shaped APIs for workflow-driven domains.
- Unbounded result sets.
- Missing versioning/deprecation strategy.
- Missing idempotency for retryable operations.
- Exposing database schemas directly.

### AI Guidance

Ask the AI to inspect contract clarity, compatibility, error semantics, idempotency, pagination, security exposure, and API/domain alignment.

---

## 3. Application Architecture & Use-Case Orchestration

### Definition

Application architecture defines how backend systems execute use cases by coordinating domain logic, persistence, external calls, transactions, validations, workflows, and side effects.

### Key Concerns

- Use-case design.
- Application services.
- Command/query separation.
- Transaction boundaries.
- Workflow orchestration.
- State machines.
- Error handling.
- Compensation logic.
- Background job coordination.

### Typical Questions

- What is the user or business intent?
- Which steps must commit atomically?
- Which steps can be asynchronous?
- Where do side effects occur?
- What happens when a downstream dependency fails?
- Is the workflow recoverable?

### Common Failure Modes

- Business logic in controllers or route handlers.
- Transaction boundaries that are too broad or too narrow.
- Side effects inside fragile transactions.
- Background jobs without idempotency or observability.
- Distributed workflows without compensation.

### AI Guidance

Ask the AI to inspect orchestration boundaries, transaction design, workflow safety, side effects, recovery paths, and misplaced logic.

---

## 4. Data Architecture & Persistence

### Definition

Data architecture defines how systems model, store, query, migrate, replicate, protect, and retire data.

### Key Concerns

- Data ownership.
- Schema design.
- Transactions and isolation.
- Consistency model.
- Migrations.
- Query patterns.
- Indexing.
- Caching.
- Replication.
- Backup/restore.
- Data retention/deletion.
- Multi-tenancy.

### Typical Questions

- Which module/service owns this data?
- What consistency does the business require?
- Can the schema evolve without downtime?
- Are indexes aligned with query patterns?
- What data must be retained, masked, archived, or deleted?
- Is caching correct under writes and invalidation?

### Common Failure Modes

- Shared database without ownership boundaries.
- Large unsafe migrations.
- Missing indexes.
- Caches without invalidation strategy.
- Reporting queries overloading production systems.
- Multi-tenant data leakage.

### AI Guidance

Ask the AI to evaluate ownership, schema, queries, transaction boundaries, consistency, migration safety, caching correctness, and lifecycle obligations.

---

## 5. Security, Identity & Trust

### Definition

Security, identity, and trust define how systems authenticate identities, authorize actions, protect resources, manage secrets, and reduce abuse.

### Key Concerns

- Authentication.
- Authorization.
- Object-level authorization.
- Function-level authorization.
- Tenant isolation.
- Secrets management.
- Transport security.
- Input/output security.
- Audit logging.
- Abuse prevention.
- Threat modeling.

### Typical Questions

- Who is making the request?
- What are they allowed to do?
- Which object/resource are they allowed to access?
- Can a user access another user’s data by changing an ID?
- Are service-to-service calls authenticated?
- Are secrets and sensitive fields protected?

### Common Failure Modes

- Authentication without authorization.
- Route-level authorization without object-level checks.
- Trusting internal network calls without service identity.
- Secrets or PII in logs.
- Missing audit trail for privileged actions.
- Tenant isolation gaps.

### AI Guidance

Ask the AI to inspect trust boundaries, authorization checks, resource ownership, secrets, sensitive data exposure, auditability, and abuse paths.

---

## 6. Validation, Correctness & Business Rule Enforcement

### Definition

Validation and correctness ensure that systems accept valid inputs, enforce business rules, preserve invariants, and reject invalid state transitions.

### Key Concerns

- Input validation.
- Schema validation.
- Business validation.
- Domain invariants.
- State transition validation.
- Cross-field validation.
- Cross-entity validation.
- Persistence constraints.
- Error reporting.

### Validation Layers

```text
Transport validation
  -> request shape, type, required fields, format

Application validation
  -> use-case preconditions and workflow constraints

Domain validation
  -> business invariants and state transitions

Persistence validation
  -> uniqueness, foreign keys, constraints, transactional guarantees
```

### Typical Questions

- Which validations belong at the API boundary?
- Which validations belong in the domain model?
- Which validations must be enforced by the database?
- Can background workers bypass domain rules?
- Are validation errors machine-readable and actionable?

### Common Failure Modes

- Relying only on frontend validation.
- Putting all validation in controllers.
- Missing persistence constraints for critical invariants.
- Allowing internal flows to bypass rules.
- Vague error messages.

### AI Guidance

Ask the AI to identify missing validations, invariant enforcement gaps, bypass paths, state transition issues, and error model inconsistencies.

---

## 7. Modularity, Dependency Architecture & Codebase Structure

### Definition

Modularity and dependency architecture define how backend code is organized, how modules depend on each other, and how infrastructure details are separated from core business logic.

### Key Concerns

- Dependency direction.
- Dependency inversion.
- Dependency injection.
- Composition root.
- Ports and adapters.
- Module boundaries.
- Package structure.
- Configuration management.
- Extensibility design.

### Conceptual Distinction

```text
Dependency Inversion = design principle.
Dependency Injection = implementation mechanism.
Ports and Adapters = architectural style.
Composition Root = place where dependencies are assembled.
```

### Typical Questions

- Does core logic depend on infrastructure?
- Are dependencies explicit or hidden?
- Are modules cohesive?
- Are there cycles?
- Can components be tested without external systems?
- Is configuration separated from code?

### Common Failure Modes

- Circular dependencies.
- Domain logic depending on database, HTTP, queue, or framework APIs.
- Global singletons.
- “Common” modules as dumping grounds.
- Too many abstractions too early.
- Hidden dependencies through static accessors.

### AI Guidance

Ask the AI to inspect dependency direction, cohesion, testability, module boundaries, abstraction quality, and infrastructure leakage.

---

## 8. Integration & Distributed Communication

### Definition

Integration and distributed communication define how systems communicate with clients, services, brokers, third-party APIs, and infrastructure components.

### Key Concerns

- Synchronous APIs.
- RPC.
- Asynchronous messaging.
- Event contracts.
- Service discovery and routing.
- API gateway and BFF.
- Retry and timeout design.
- Circuit breakers.
- Bulkheads.
- Backpressure.
- Idempotent consumers.
- Outbox/inbox patterns.

### Typical Questions

- Should this interaction be synchronous or asynchronous?
- What is the timeout?
- Is retry safe?
- Is the operation idempotent?
- How are duplicate messages handled?
- How are schemas versioned?
- What happens under partial failure?

### Common Failure Modes

- Retrying non-idempotent operations.
- Missing timeouts.
- Retry storms.
- Assuming exactly-once delivery.
- Breaking consumers with incompatible event changes.
- Gateway accumulating business logic.

### AI Guidance

Ask the AI to evaluate communication style, retry safety, timeouts, duplicate handling, contracts, event publishing reliability, and failure modes.

---

## 9. Reliability, Resilience & Availability

### Definition

Reliability and resilience define whether the backend continues to deliver acceptable behavior under failure, load, dependency degradation, and incidents.

### Key Concerns

- Availability.
- Fault tolerance.
- Graceful degradation.
- Timeout and retry policies.
- Circuit breakers.
- Bulkhead isolation.
- Disaster recovery.
- SLOs and error budgets.
- Incident response.
- Resilience testing.

### Reliability Concepts

```text
Reliability = system performs correctly from the user’s perspective.
Availability = system can serve requests.
Resilience = system can absorb, recover from, or degrade under failure.
Durability = committed data is not lost.
Recoverability = system can be restored after failure.
```

### Typical Questions

- What is the user-visible reliability target?
- What are the critical user journeys?
- What dependencies can fail?
- What is the fallback behavior?
- What is the RPO/RTO?
- What alerts indicate user impact?

### Common Failure Modes

- No explicit SLO.
- Monitoring technical symptoms but not user impact.
- Aggressive retries during outages.
- Missing fallback behavior.
- Shared resource pools causing cascading failure.
- Untested restore process.

### AI Guidance

Ask the AI to reason about user-visible failures, SLOs, dependencies, retry/circuit breaker/bulkhead behavior, recovery, and disaster assumptions.

---

## 10. Performance, Scalability & Efficiency

### Definition

Performance and scalability define how systems handle load, latency, throughput, resource consumption, growth, and cost-performance trade-offs.

### Key Concerns

- Latency: p50, p90, p95, p99.
- Throughput.
- Capacity planning.
- Resource efficiency.
- Database performance.
- Caching.
- Concurrency.
- Horizontal scaling.
- Load testing.
- Cost-performance trade-offs.

### Performance Engineering Loop

```text
Measure
  -> Identify bottleneck
  -> Form hypothesis
  -> Optimize
  -> Validate
  -> Monitor regression
```

### Typical Questions

- What is the target p95/p99 latency?
- What is expected and peak throughput?
- Which resource saturates first?
- Is the bottleneck CPU, memory, DB, network, lock contention, or dependency latency?
- Is caching safe and useful?
- Can the system scale horizontally?

### Common Failure Modes

- Optimizing without measurement.
- Looking only at average latency.
- Ignoring tail latency.
- Unbounded concurrency.
- Chatty database access.
- Cache without correctness.
- One-time load testing.

### AI Guidance

Ask the AI to assess latency, throughput, bottlenecks, queries, indexes, cache trade-offs, concurrency, load tests, and cost.

---

## 11. Observability, Monitoring & Alerting

### Definition

Observability is the ability to understand system behavior from emitted signals. Monitoring uses those signals to detect known failure modes and user-impacting conditions.

### Key Concerns

- Metrics.
- Logs.
- Traces.
- Alerts.
- Dashboards.
- Runbooks.
- Telemetry standards.
- Audit observability.
- Business observability.

### Observability Signals

```text
Metrics -> rates, errors, latency, saturation, business KPIs
Logs    -> structured events, correlation IDs, sensitive data filtering
Traces  -> request flow, spans, dependency latency, context propagation
Alerts  -> actionable user-impacting conditions
Runbooks -> diagnosis and mitigation guidance
```

### Typical Questions

- What are the golden signals?
- Can user-impacting failures be detected?
- Can logs, metrics, and traces be correlated?
- Are high-cardinality labels controlled?
- Are alerts actionable?
- Is sensitive data excluded from telemetry?

### Common Failure Modes

- Many dashboards but no actionable alerts.
- Logs without correlation IDs.
- High-cardinality metrics.
- Alert fatigue.
- Missing traces across boundaries.
- Secrets or PII in logs.
- No runbook for critical alerts.

### AI Guidance

Ask the AI to inspect metrics, logs, traces, alert quality, dashboard usefulness, runbooks, correlation, and sensitive data handling.

---

## 12. Delivery, Operations & Runtime Management

### Definition

Delivery and operations define how backend systems are built, tested, deployed, configured, observed, operated, and recovered in production.

### Key Concerns

- CI/CD.
- Release strategy.
- Environment strategy.
- Configuration management.
- Health checks.
- Runtime controls.
- Incident management.
- Backup and restore.
- Change management.
- Operational documentation.

### Typical Questions

- Is deployment repeatable?
- Can a bad release be rolled back quickly?
- Are migrations backward compatible?
- Are feature flags available for risky changes?
- Are health checks meaningful?
- Are production configs controlled and audited?

### Common Failure Modes

- Manual deployment steps.
- Unsafe migrations.
- No rollback.
- Weak health checks.
- Feature flags without cleanup.
- Secrets in code or artifacts.
- No incident review process.

### AI Guidance

Ask the AI to review CI/CD safety, release/rollback, environment config, migration rollout, operational readiness, and runbooks.

---

## 13. Testing, Verification & Quality Engineering

### Definition

Testing and verification prove that backend behavior is correct under expected, edge-case, failure, performance, and security conditions.

### Key Concerns

- Unit testing.
- Integration testing.
- Contract testing.
- End-to-end testing.
- Property-based testing.
- Performance testing.
- Security testing.
- Resilience testing.
- Migration testing.
- Observability testing.

### Testing Shape

```text
Many fast tests:
  - Unit tests
  - Domain tests
  - Pure function tests

Fewer integration tests:
  - Database tests
  - Adapter tests
  - Queue/cache tests

Few end-to-end tests:
  - Critical user journeys

Specialized tests:
  - Contract, performance, security, resilience, migration, observability tests
```

### Typical Questions

- Which behavior is critical enough to test?
- Which invariants must never regress?
- Are external contracts tested?
- Are failure modes tested?
- Are migrations tested?
- Are tests deterministic?

### Common Failure Modes

- Only happy-path tests.
- Over-mocking.
- No contract tests.
- Slow/flaky E2E tests.
- Missing migration tests.
- No failure-mode tests.
- No telemetry verification.

### AI Guidance

Ask the AI to plan or review tests for rules, persistence, adapters, contracts, failure modes, migrations, performance, resilience, and observability.

---

## 14. Governance, Privacy, Compliance & Risk

### Definition

Governance, privacy, compliance, and risk define how backend systems satisfy organizational, legal, security, privacy, cost, and operational obligations.

### Key Concerns

- Privacy engineering.
- Sensitive data classification.
- Compliance.
- Auditability.
- Data governance.
- Policy enforcement.
- Risk management.
- Cost governance.
- Architecture governance.
- Vendor governance.

### Typical Questions

- Does the system process sensitive data?
- What retention and deletion rules apply?
- Who owns the data and service?
- Are privileged actions auditable?
- Are compliance controls testable?
- Are vendors or third-party dependencies involved?

### Common Failure Modes

- Compliance after release.
- No clear data owner.
- Storing more data than needed.
- Missing deletion/retention.
- Missing audit trail.
- No ADRs for important decisions.
- Ignoring vendor and supply-chain risk.

### AI Guidance

Ask the AI to check privacy, retention, audit logs, policy enforcement, compliance evidence, vendor risks, and architecture decisions.

---

## 15. Applied AI Backend Engineering

### Definition

Applied AI backend engineering covers backend concerns required to build, expose, operate, evaluate, and govern AI-powered capabilities.

### Key Concerns

- AI use-case design.
- Model serving.
- Prompt engineering.
- Context engineering.
- RAG architecture.
- Tool/function calling.
- Agent workflows.
- Evaluation.
- AI observability.
- AI safety and security.
- Human-in-the-loop.
- AI governance.

### Typical Questions

- Is AI needed, or would deterministic logic be safer?
- What is the quality bar?
- How is output evaluated?
- What data is sent to the model?
- Can the model call tools or trigger side effects?
- What happens if the model hallucinates?
- How are prompt injection, data leakage, latency, and cost handled?

### Common Failure Modes

- AI feature shipped without evaluation.
- Unversioned prompts.
- Sensitive data sent unnecessarily.
- Tool side effects without approval.
- No monitoring for cost, latency, quality, or drift.
- No fallback when providers fail.
- Trusting AI output without validation.

### AI Guidance

Ask the AI to analyze AI appropriateness, prompt/context quality, retrieval, evaluation, tool boundaries, privacy, observability, cost, safety, and human review.

---

## Cross-Scope Routing Notes

The 15 scopes compress into the active 9-scope library as follows:

| 15-Scope Model                                              | 9-Scope Skill Routing                                                 |
| ----------------------------------------------------------- | --------------------------------------------------------------------- |
| 1. Domain & Business Capability Design                      | `backend-domain-and-api-design`                                       |
| 2. API & Interface Design                                   | `backend-domain-and-api-design`                                       |
| 3. Application Architecture & Use-Case Orchestration        | `backend-application-architecture`                                    |
| 4. Data Architecture & Persistence                          | `backend-data-and-persistence`                                        |
| 5. Security, Identity & Trust                               | `backend-security-and-trust`                                          |
| 6. Validation, Correctness & Business Rule Enforcement      | `backend-domain-and-api-design` or `backend-application-architecture` |
| 7. Modularity, Dependency Architecture & Codebase Structure | `backend-application-architecture`                                    |
| 8. Integration & Distributed Communication                  | `backend-integration-and-distributed-communication`                   |
| 9. Reliability, Resilience & Availability                   | `backend-reliability-and-resilience`                                  |
| 10. Performance, Scalability & Efficiency                   | `backend-performance-and-scalability`                                 |
| 11. Observability, Monitoring & Alerting                    | `backend-observability-and-operations`                                |
| 12. Delivery, Operations & Runtime Management               | `backend-observability-and-operations`                                |
| 13. Testing, Verification & Quality Engineering             | `backend-ai-governance-and-quality` or selected implementation scope  |
| 14. Governance, Privacy, Compliance & Risk                  | `backend-ai-governance-and-quality` or `backend-security-and-trust`   |
| 15. Applied AI Backend Engineering                          | `backend-ai-governance-and-quality`                                   |
