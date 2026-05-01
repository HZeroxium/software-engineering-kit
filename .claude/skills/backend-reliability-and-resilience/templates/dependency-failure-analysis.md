# Dependency Failure Analysis

## Dependency

`<dependency>`

## Dependency Role

`<what the dependency provides>`

## Failure Types

| Failure         | User Impact | Detection  | Mitigation     |
| --------------- | ----------- | ---------- | -------------- |
| Timeout         | `<impact>`  | `<signal>` | `<mitigation>` |
| Error response  | `<impact>`  | `<signal>` | `<mitigation>` |
| Partial success | `<impact>`  | `<signal>` | `<mitigation>` |
| Stale data      | `<impact>`  | `<signal>` | `<mitigation>` |
| Rate limit      | `<impact>`  | `<signal>` | `<mitigation>` |
| Outage          | `<impact>`  | `<signal>` | `<mitigation>` |

## Fallback / Degradation

- **Can degrade:** `<yes/no>`
- **Degraded behavior:** `<behavior>`
- **User communication:** `<response/error/status>`

## Recovery

- **Automatic recovery:** `<yes/no/unknown>`
- **Manual repair:** `<steps/unknown>`
- **Reconciliation needed:** `<yes/no>`

## Tests

- `<dependency timeout test>`
- `<dependency error test>`
- `<fallback test>`
