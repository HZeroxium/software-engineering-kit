# Data Design Review

## Summary

- **Data area:** `<area>`
- **Owner:** `<module/service/team if known>`
- **Storage type:** `<relational/document/cache/object/etc.>`
- **Risk level:** `<low/medium/high/critical>`
- **Recommendation:** `<approve / revise / block>`

## Confirmed Facts

- `<fact>` — Evidence: `<source>`

## Data Ownership

| Data                      | Owner     | Access Pattern | Notes     |
| ------------------------- | --------- | -------------- | --------- |
| `<entity/table/document>` | `<owner>` | `<read/write>` | `<notes>` |

## Data Model

| Field / Attribute | Type     |  Required? | Constraints     | Notes     |
| ----------------- | -------- | ---------: | --------------- | --------- |
| `<field>`         | `<type>` | `<yes/no>` | `<constraints>` | `<notes>` |

## Query Patterns

| Query     | Frequency           | Index Needed? | Risk     |
| --------- | ------------------- | ------------: | -------- |
| `<query>` | `<low/medium/high>` |    `<yes/no>` | `<risk>` |

## Consistency

- **Required consistency:** `<strong/eventual/read-your-writes/etc.>`
- **Transaction boundary:** `<boundary>`
- **Concurrency control:** `<optimistic/pessimistic/none/unknown>`

## Migration Impact

- **Migration needed:** `<yes/no/unknown>`
- **Backward compatible:** `<yes/no/unknown>`
- **Rollback strategy:** `<strategy>`

## Cache Impact

- **Cache involved:** `<yes/no>`
- **Invalidation:** `<strategy>`
- **Staleness tolerance:** `<tolerance>`

## Retention / Deletion / Privacy

- `<consideration>`

## Validation

- `<test/query plan/migration test/load test/manual review>`
