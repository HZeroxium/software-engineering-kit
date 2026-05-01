# Domain and API Design Report

## Summary

- **Feature / capability:** `<name>`
- **Primary actor(s):** `<actors>`
- **Primary domain area:** `<domain>`
- **API/interface type:** `<HTTP/RPC/event/job/internal module/etc.>`
- **Risk level:** `<low/medium/high/critical>`
- **Implementation readiness:** `<ready / needs clarification / blocked>`

## Confirmed Facts

- `<fact>` — Evidence: `<source>`

## Assumptions

- `<assumption>`

## Open Questions

1. `<question>`
2. `<question>`

## Domain Model Summary

| Concept     | Type                                            | Responsibility     | Notes     |
| ----------- | ----------------------------------------------- | ------------------ | --------- |
| `<concept>` | `<entity/value object/aggregate/event/service>` | `<responsibility>` | `<notes>` |

## Business Rules and Invariants

| Rule / Invariant | Enforcement Layer                      | Failure Mode | Test Case |
| ---------------- | -------------------------------------- | ------------ | --------- |
| `<rule>`         | `<API/application/domain/persistence>` | `<failure>`  | `<test>`  |

## State Transitions

| Current State | Command / Event | Next State |     Valid? | Guard    |
| ------------- | --------------- | ---------- | ---------: | -------- |
| `<state>`     | `<command>`     | `<state>`  | `<yes/no>` | `<rule>` |

## API / Interface Design

### Contract Sketch

```text
<request/response/event/interface sketch>
```

### Validation Boundary

| Validation     | Layer                                        | Error     |
| -------------- | -------------------------------------------- | --------- |
| `<validation>` | `<transport/application/domain/persistence>` | `<error>` |

## Error Model

| Error     | Type                              | HTTP/RPC/Event Mapping | Retryable? | Client Action |
| --------- | --------------------------------- | ---------------------- | ---------: | ------------- |
| `<error>` | `<validation/business/technical>` | `<mapping>`            | `<yes/no>` | `<action>`    |

## Idempotency and Retry Safety

- **Required:** `<yes/no>`
- **Idempotency key:** `<key>`
- **Deduplication window:** `<window>`
- **Duplicate request behavior:** `<behavior>`
- **Retryable errors:** `<errors>`
- **Non-retryable errors:** `<errors>`

## Compatibility and Versioning

- **Breaking change:** `<yes/no>`
- **Backward-compatible path:** `<strategy>`
- **Deprecation needed:** `<yes/no>`
- **Migration required for clients:** `<yes/no>`

## Pagination / Filtering / Sorting

- **Pagination style:** `<offset/cursor/keyset/none>`
- **Filtering constraints:** `<constraints>`
- **Sorting constraints:** `<constraints>`
- **Performance risk:** `<risk>`

## Test and Validation Strategy

| Test     | Purpose      |
| -------- | ------------ |
| `<test>` | `<behavior>` |

## Final Recommendation

`<recommended design or review conclusion>`
