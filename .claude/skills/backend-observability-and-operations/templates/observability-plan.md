# Observability Plan

## Scope

`<feature/API/job/service>`

## Operational Goal

`<what operators must detect/diagnose/recover>`

## Signals

| Signal  |  Required? | Purpose     |
| ------- | ---------: | ----------- |
| Logs    | `<yes/no>` | `<purpose>` |
| Metrics | `<yes/no>` | `<purpose>` |
| Traces  | `<yes/no>` | `<purpose>` |
| Alerts  | `<yes/no>` | `<purpose>` |
| Runbook | `<yes/no>` | `<purpose>` |

## Logging Plan

- `<event/outcome/context>`
- Sensitive fields excluded: `<fields>`

## Metrics Plan

| Metric Concept | Type                             | Labels / Dimensions | Cardinality Risk |
| -------------- | -------------------------------- | ------------------- | ---------------- |
| `<concept>`    | `<counter/gauge/histogram/etc.>` | `<labels>`          | `<risk>`         |

## Tracing Plan

- `<span/boundary/context propagation>`

## Alert / Runbook Plan

- **Alert condition:** `<condition>`
- **User impact:** `<impact>`
- **Runbook action:** `<action>`

## Validation

- `<unit/integration/manual telemetry review>`
