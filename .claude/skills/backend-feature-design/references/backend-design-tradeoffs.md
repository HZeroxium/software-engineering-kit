# Backend Design Trade-Offs

## Purpose

Use this reference to make design choices explicit.

## Common Trade-Offs

| Trade-Off                                      | Option A                                | Option B                                            | Key Question                              |
| ---------------------------------------------- | --------------------------------------- | --------------------------------------------------- | ----------------------------------------- |
| Sync vs async                                  | Immediate response, simpler consistency | Better resilience, eventual consistency             | Does caller need immediate final result?  |
| Strong vs eventual consistency                 | Simpler correctness                     | Better availability/scalability                     | What does the business require?           |
| Centralized vs decentralized ownership         | Easier coordination                     | Better autonomy                                     | Who owns the data/capability?             |
| Generic abstraction vs concrete implementation | Flexible                                | Simpler                                             | Is variation real or speculative?         |
| Cache vs direct read                           | Lower latency/load                      | Simpler correctness                                 | Can stale data be tolerated?              |
| Broad transaction vs narrow transaction        | Easier atomicity                        | Less lock contention                                | What must truly be atomic?                |
| Reuse existing API vs new API                  | Less surface area                       | Better contract clarity                             | Is the existing API semantically correct? |
| Framework-native vs internal wrapper           | Faster implementation                   | Better consistency/safety if wrapper encodes policy | What does repo evidence show?             |
| More observability vs lower cost/privacy risk  | Easier debugging                        | Lower cost/exposure                                 | Which signals are actionable and safe?    |

## Decision Record Pattern

Use:

```text
Decision:
<selected option>

Context:
<why this decision exists>

Alternatives:
<option A, option B>

Rationale:
<why selected>

Trade-offs:
<accepted downsides>

Validation:
<how to verify>

Rollback:
<how to change later>
```
