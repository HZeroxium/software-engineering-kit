# Retry, Timeout, and Idempotency Analysis

## Operation

`<operation / API / message / external call>`

## Operation Type

- [ ] Read-only
- [ ] Local write
- [ ] External write
- [ ] Message publish
- [ ] Message consume
- [ ] Workflow step
- [ ] Unknown

## Timeout / Deadline

| Layer      | Policy               | Evidence / Notes |
| ---------- | -------------------- | ---------------- |
| Caller     | `<timeout/deadline>` | `<notes>`        |
| Backend    | `<timeout/deadline>` | `<notes>`        |
| Downstream | `<timeout/deadline>` | `<notes>`        |

## Retry Policy

| Failure     |     Retry? | Backoff    | Limit     | Risk     |
| ----------- | ---------: | ---------- | --------- | -------- |
| `<failure>` | `<yes/no>` | `<policy>` | `<limit>` | `<risk>` |

## Idempotency

- **Required:** `<yes/no>`
- **Idempotency key:** `<key>`
- **Deduplication scope:** `<user/tenant/resource/global>`
- **Deduplication storage:** `<storage>`
- **Concurrent duplicate behavior:** `<behavior>`

## Retry Safety Decision

`<safe / unsafe / safe only with conditions>`

## Risks

- `<duplicate side effect>`
- `<retry storm>`
- `<timeout hides success>`
- `<partial failure>`
- `<dependency overload>`

## Validation

- `<timeout test>`
- `<retry exhaustion test>`
- `<duplicate request test>`
- `<concurrent duplicate test>`
