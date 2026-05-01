# Framework-Agnostic Backend Principles

## Purpose

Use these principles when analyzing backend systems without assuming a specific framework, vendor, cloud, or internal platform.

## Core Principles

### 1. Start From Business Capability

Do not start from controllers, tables, queues, or frameworks. Identify the business capability, actors, operations, invariants, and ownership boundaries first.

### 2. Separate Contract From Implementation

APIs, events, and RPC interfaces are contracts. They should not expose internal schema, framework types, or accidental implementation details.

### 3. Make State Changes Explicit

State transitions, transactions, side effects, retries, compensation, and idempotency should be visible in the design.

### 4. Treat Data Ownership as Architecture

Data ownership determines consistency, APIs, migrations, access control, and operational responsibility.

### 5. Security Is a Design Boundary

Authentication, authorization, object-level access control, tenant isolation, secrets, and audit logs are not optional add-ons.

### 6. Assume Networks and Dependencies Fail

Distributed calls need timeouts, retries, circuit breakers, bulkheads, idempotency, and observability.

### 7. Measure Before Optimizing

Performance work should start with metrics, traces, query plans, profiling, or load tests.

### 8. Design for Operation

A backend feature is incomplete without validation, logs, metrics, traces, alerts, configuration, rollout, rollback, and runbook considerations where relevant.

### 9. Prefer Existing Internal Abstractions When Confirmed

In internal organization repositories, existing wrappers may encode security, observability, config, RPC, or lifecycle conventions. Do not bypass them unless the repository evidence and user confirm it is safe.

### 10. Do Not Invent Internal Library Behavior

For internal libraries:

- Search actual usage.
- Prefer tests and examples.
- Mark unknowns explicitly.
- Ask for internal docs when needed.

### 11. Use Java Examples Without Assuming Spring

Java examples may mention:

- Interfaces.
- Records.
- Services/use cases.
- Repositories/ports.
- Transactions.
- Factories/composition roots.
- Executors/thread pools.
- Tests.

Do not assume:

- Spring Boot.
- JPA/Hibernate.
- Maven/Gradle behavior beyond repo evidence.
- Specific annotations.
- Internal framework lifecycle.

### 12. Make Validation Evidence Explicit

Every recommendation should identify how to verify it:

- Tests.
- Type checking.
- Static analysis.
- Build command.
- Logs.
- Metrics.
- Traces.
- Load tests.
- Security tests.
- Review checklist.

## Minimal Backend Reasoning Sequence

Use this sequence for broad tasks:

```text
1. What business capability is involved?
2. What API/interface or workflow exposes it?
3. What data is read or written?
4. What security/trust boundary exists?
5. What integration boundaries exist?
6. What can fail?
7. What must be measured?
8. What must be tested?
9. What needs human approval?
```

## Java-Neutral Example Pattern

```text
Transport/API layer:
  - Parses request
  - Authenticates caller
  - Performs basic request validation
  - Calls application use case
  - Maps result/error to contract response

Application/use-case layer:
  - Coordinates workflow
  - Starts/ends transaction if needed
  - Calls domain logic
  - Calls persistence ports/adapters
  - Emits events or schedules side effects safely

Domain layer:
  - Enforces business invariants
  - Owns valid state transitions
  - Avoids framework and infrastructure dependencies

Infrastructure/adapters:
  - Database access
  - RPC/HTTP clients
  - Messaging
  - Cache
  - File/object storage
  - Internal platform wrappers
```
