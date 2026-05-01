# Backend Feature Design Document

## 1. Summary

- **Feature:** `<feature name>`
- **Business capability:** `<capability>`
- **Primary backend scope:** `<scope>`
- **Secondary scopes:** `<scopes>`
- **Risk level:** `<low/medium/high/critical>`
- **Implementation readiness:** `<ready / blocked / needs clarification>`

## 2. Problem Framing

### User / Business Intent

`<what the feature enables>`

### Current Behavior

`<current behavior if known>`

### Desired Behavior

`<target behavior>`

### Out of Scope

- `<non-goal>`
- `<non-goal>`

## 3. Domain Concepts

| Concept     | Type                            | Responsibility     | Notes     |
| ----------- | ------------------------------- | ------------------ | --------- |
| `<concept>` | `<entity/value/workflow/event>` | `<responsibility>` | `<notes>` |

## 4. Business Rules and Invariants

- `<rule>`
- `<rule>`

## 5. API / Interface Design

### Interface Type

- [ ] HTTP API
- [ ] RPC
- [ ] Event
- [ ] Message consumer
- [ ] CLI
- [ ] Internal module interface
- [ ] Background job
- [ ] Other: `<type>`

### Contract

```text
<request/response/event/interface sketch>
```

### Error Model

| Error     | Type                              | Retryable? | Client Action |
| --------- | --------------------------------- | ---------: | ------------- |
| `<error>` | `<business/validation/technical>` | `<yes/no>` | `<action>`    |

### Compatibility

- **Breaking changes:** `<yes/no>`
- **Versioning needed:** `<yes/no>`
- **Deprecation needed:** `<yes/no>`

## 6. Application Workflow

```text
1. <step>
2. <step>
3. <step>
```

### Transaction Boundary

`<what must commit atomically>`

### Side Effects

| Side Effect                   | Timing                               | Idempotency Requirement | Recovery     |
| ----------------------------- | ------------------------------------ | ----------------------- | ------------ |
| `<event/email/provider call>` | `<inside/outside transaction/async>` | `<requirement>`         | `<recovery>` |

## 7. Data / Persistence Impact

| Data Area                    | Change     | Ownership | Consistency Requirement |
| ---------------------------- | ---------- | --------- | ----------------------- |
| `<table/entity/cache/index>` | `<change>` | `<owner>` | `<requirement>`         |

### Migration Needed

- [ ] No
- [ ] Yes, backward-compatible expand-contract required
- [ ] Unknown

## 8. Security and Trust

| Concern             | Design Decision | Risk     |
| ------------------- | --------------- | -------- |
| Authentication      | `<decision>`    | `<risk>` |
| Authorization       | `<decision>`    | `<risk>` |
| Object-level access | `<decision>`    | `<risk>` |
| Tenant isolation    | `<decision>`    | `<risk>` |
| Secrets             | `<decision>`    | `<risk>` |
| Audit logging       | `<decision>`    | `<risk>` |
| Sensitive data      | `<decision>`    | `<risk>` |

## 9. Integration and Distributed Communication

| Integration                 | Style          | Timeout     | Retry      | Idempotency | Failure Handling |
| --------------------------- | -------------- | ----------- | ---------- | ----------- | ---------------- |
| `<service/provider/broker>` | `<sync/async>` | `<timeout>` | `<policy>` | `<policy>`  | `<behavior>`     |

## 10. Reliability, Performance, and Observability

### Reliability

- `<fallback/degradation/recovery behavior>`

### Performance

- `<latency/throughput/capacity assumption>`

### Observability

| Signal  |  Required? | Details     |
| ------- | ---------: | ----------- |
| Metrics | `<yes/no>` | `<details>` |
| Logs    | `<yes/no>` | `<details>` |
| Traces  | `<yes/no>` | `<details>` |
| Alerts  | `<yes/no>` | `<details>` |
| Runbook | `<yes/no>` | `<details>` |

## 11. Test and Validation Strategy

| Test Type     |  Required? | What to Validate |
| ------------- | ---------: | ---------------- |
| Unit          | `<yes/no>` | `<behavior>`     |
| Integration   | `<yes/no>` | `<behavior>`     |
| Contract      | `<yes/no>` | `<behavior>`     |
| E2E           | `<yes/no>` | `<behavior>`     |
| Security      | `<yes/no>` | `<behavior>`     |
| Performance   | `<yes/no>` | `<behavior>`     |
| Observability | `<yes/no>` | `<behavior>`     |

## 12. Risks

| Risk     | Severity                     | Mitigation     |
| -------- | ---------------------------- | -------------- |
| `<risk>` | `<low/medium/high/critical>` | `<mitigation>` |

## 13. Open Questions

1. `<question>`
2. `<question>`
3. `<question>`

## 14. Handoff to Implementation

```text
Use backend-feature-implementation.

Task:
<implementation task>

Design summary:
<summary>

Affected scopes:
<scopes>

Risks:
<risks>

Validation expectations:
<tests/build/lint/static analysis/CI/logs/metrics/manual review>

Constraints:
- Framework-agnostic unless repo evidence confirms a framework.
- Do not invent internal library behavior.
- Preserve public contracts unless explicitly changing them.
```
