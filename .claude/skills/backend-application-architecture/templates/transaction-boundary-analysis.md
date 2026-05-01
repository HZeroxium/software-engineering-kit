# Transaction Boundary Analysis

## Operation

`<operation/use case>`

## State Changes

| State Change | Resource                | Must Be Atomic? | Reason     |
| ------------ | ----------------------- | --------------: | ---------- |
| `<change>`   | `<DB/cache/event/etc.>` |      `<yes/no>` | `<reason>` |

## Proposed Transaction Boundary

```text
Begin transaction
  - <step>
  - <step>
Commit transaction
After commit
  - <side effect>
```

## External Calls

| Call     | Inside Transaction? | Risk     | Recommendation     |
| -------- | ------------------: | -------- | ------------------ |
| `<call>` |          `<yes/no>` | `<risk>` | `<recommendation>` |

## Consistency Model

- **Required consistency:** `<strong/eventual/read-your-writes/etc.>`
- **Acceptable stale state:** `<yes/no>`
- **Recovery mechanism:** `<outbox/retry/reconciliation/manual/etc.>`

## Failure Matrix

| Failure Point | Result     | Mitigation     |
| ------------- | ---------- | -------------- |
| `<failure>`   | `<result>` | `<mitigation>` |

## Validation

- `<transaction test>`
- `<concurrency test>`
- `<failure-mode test>`
