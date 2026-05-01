# Distributed Failure Mode Report

## Scope

`<integration/workflow>`

## Critical Path

```text
<caller> -> <service A> -> <dependency/event/provider> -> <result>
```

## Failure Mode Matrix

| Failure     | User Impact | Internal Impact | Mitigation     | Observability |
| ----------- | ----------- | --------------- | -------------- | ------------- |
| `<failure>` | `<impact>`  | `<impact>`      | `<mitigation>` | `<signal>`    |

## Partial Failure Risks

- `<risk>`

## Retry Amplification Risks

- `<risk>`

## Duplicate Side Effect Risks

- `<risk>`

## Recovery Strategy

- `<automatic retry / reconciliation / compensation / manual repair / DLQ replay>`

## Tests

- `<failure injection test>`
- `<duplicate delivery test>`
- `<recovery test>`
