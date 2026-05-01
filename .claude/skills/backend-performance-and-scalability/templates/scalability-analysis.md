# Scalability Analysis

## Scope

`<service/API/job/workflow>`

## Growth Dimension

| Dimension     | Current           | Expected Growth | Risk     |
| ------------- | ----------------- | --------------- | -------- |
| Requests      | `<value/unknown>` | `<growth>`      | `<risk>` |
| Data volume   | `<value/unknown>` | `<growth>`      | `<risk>` |
| Tenants/users | `<value/unknown>` | `<growth>`      | `<risk>` |
| Jobs/messages | `<value/unknown>` | `<growth>`      | `<risk>` |

## Scalability Limiters

| Limiter                            | Why It Limits | Mitigation     |
| ---------------------------------- | ------------- | -------------- |
| `<DB/query/pool/cache/dependency>` | `<reason>`    | `<mitigation>` |

## Horizontal Scaling

- **Stateless path:** `<yes/no/unknown>`
- **Shared bottleneck:** `<DB/cache/provider/etc.>`
- **Partitioning/sharding need:** `<yes/no/unknown>`

## Cost-Performance Concerns

- `<concern>`

## Validation

- `<load test>`
- `<capacity model>`
- `<resource saturation metrics>`
