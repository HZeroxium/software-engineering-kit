# Resilience Design Plan

## Scope

`<feature/service/workflow>`

## Resilience Goal

`<what should remain true under failure>`

## Failure Assumptions

- `<failure assumption>`

## Controls

| Control         | Design        | Validation      |
| --------------- | ------------- | --------------- |
| Timeout         | `<policy>`    | `<test>`        |
| Retry           | `<policy>`    | `<test>`        |
| Circuit breaker | `<policy>`    | `<test>`        |
| Bulkhead        | `<isolation>` | `<test>`        |
| Backpressure    | `<policy>`    | `<test>`        |
| Fallback        | `<behavior>`  | `<test>`        |
| Reconciliation  | `<process>`   | `<test/manual>` |

## Degraded Mode

- **Trigger:** `<condition>`
- **Behavior:** `<behavior>`
- **User impact:** `<impact>`
- **Observability:** `<signals>`

## Rollback / Disable Path

`<feature flag/config/rollback/manual process>`

## Open Questions

- `<question>`
