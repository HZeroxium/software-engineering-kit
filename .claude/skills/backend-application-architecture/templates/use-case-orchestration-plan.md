# Use-Case Orchestration Plan

## Use Case

`<use case>`

## Command / Query Classification

- **Type:** `<command/query/workflow/job>`
- **Mutates state:** `<yes/no>`
- **Requires transaction:** `<yes/no/unknown>`
- **Has external side effects:** `<yes/no>`

## Orchestration Flow

```text
1. <step>
2. <step>
3. <step>
```

## Responsibility Assignment

| Step     | Layer / Component                         | Responsibility     |
| -------- | ----------------------------------------- | ------------------ |
| `<step>` | `<API/application/domain/infrastructure>` | `<responsibility>` |

## Transaction Boundary

`<what must be atomic>`

## Side Effects

| Side Effect | Timing                                            | Safe Handling |
| ----------- | ------------------------------------------------- | ------------- |
| `<effect>`  | `<inside/outside transaction/after commit/async>` | `<strategy>`  |

## Failure Handling

| Failure     | Handling     | Retryable? |
| ----------- | ------------ | ---------: |
| `<failure>` | `<handling>` | `<yes/no>` |

## Tests

- `<test>`
- `<test>`
