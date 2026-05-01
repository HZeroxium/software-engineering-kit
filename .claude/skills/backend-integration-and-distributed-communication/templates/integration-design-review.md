# Integration Design Review

## Summary

- **Integration:** `<caller -> callee>`
- **Style:** `<sync / async / webhook / event / RPC / internal API>`
- **Risk level:** `<low/medium/high/critical>`
- **Recommendation:** `<approve / revise / block>`

## Confirmed Facts

- `<fact>` — Evidence: `<source>`

## Assumptions

- `<assumption>`

## Communication Style

| Area               | Decision                    | Reason     |
| ------------------ | --------------------------- | ---------- |
| Style              | `<sync/async/etc.>`         | `<reason>` |
| Contract owner     | `<owner>`                   | `<reason>` |
| Caller expectation | `<immediate/eventual>`      | `<reason>` |
| Failure visibility | `<caller/backend/operator>` | `<reason>` |

## Contract / Schema

```text
<request/response/event/message sketch>
```

## Timeout / Retry / Deadline

| Concern              | Decision                 | Risk     |
| -------------------- | ------------------------ | -------- |
| Timeout              | `<value/policy/unknown>` | `<risk>` |
| Retry                | `<policy/none/unknown>`  | `<risk>` |
| Deadline propagation | `<yes/no/unknown>`       | `<risk>` |
| Cancellation         | `<behavior>`             | `<risk>` |

## Idempotency and Duplicate Handling

- **Required:** `<yes/no>`
- **Key:** `<idempotency key / message ID / natural key>`
- **Duplicate behavior:** `<ignore / return prior result / conflict / compensate>`
- **Storage:** `<dedupe table / inbox / unique constraint / unknown>`

## Failure Modes

| Failure     | Impact     | Mitigation     | Test     |
| ----------- | ---------- | -------------- | -------- |
| `<failure>` | `<impact>` | `<mitigation>` | `<test>` |

## Observability

- **Metrics:** `<rate/error/duration/backlog/retry/failure>`
- **Logs:** `<correlation IDs, outcome, safe fields>`
- **Traces:** `<boundary spans if supported>`
- **Alerts:** `<user-impacting condition>`

## Open Questions

1. `<question>`
2. `<question>`
