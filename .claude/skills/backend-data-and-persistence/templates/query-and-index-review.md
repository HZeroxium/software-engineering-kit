# Query and Index Review

## Query

```text
<query or repository method>
```

## Access Pattern

- **Caller:** `<caller>`
- **Frequency:** `<low/medium/high>`
- **Cardinality:** `<expected size>`
- **Latency sensitivity:** `<low/medium/high>`

## Filters and Sorts

| Field     | Usage                |           Indexed? | Notes     |
| --------- | -------------------- | -----------------: | --------- |
| `<field>` | `<filter/sort/join>` | `<yes/no/unknown>` | `<notes>` |

## Index Recommendation

```text
<index recommendation>
```

## Risks

- `<full scan>`
- `<deep pagination>`
- `<lock contention>`
- `<hot partition>`
- `<tenant filter missing>`
- `<N+1 query>`

## Validation

- `<explain plan>`
- `<integration test>`
- `<load test>`
- `<metrics/traces>`
