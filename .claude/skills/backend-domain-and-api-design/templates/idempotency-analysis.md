# Idempotency Analysis

## Operation

`<operation/API/message/job>`

## Idempotency Required?

- **Required:** `<yes/no>`
- **Reason:** `<client retry / timeout / duplicate message / payment / job / notification / external side effect>`

## Side Effects

| Side Effect     | Duplicate Risk | Idempotency Strategy |
| --------------- | -------------- | -------------------- |
| `<side effect>` | `<risk>`       | `<strategy>`         |

## Idempotency Key

- **Source:** `<client-provided / natural key / message ID / generated>`
- **Scope:** `<user/tenant/resource/global>`
- **Deduplication window:** `<duration>`
- **Stored result:** `<yes/no>`
- **Duplicate response behavior:** `<same result / conflict / ignored / no-op>`

## Retry Safety

| Failure     |     Safe to Retry? | Reason     |
| ----------- | -----------------: | ---------- |
| `<failure>` | `<yes/no/unknown>` | `<reason>` |

## Data Constraints

- `<unique constraint / dedup table / idempotency table / inbox table>`

## Validation

- `<duplicate request test>`
- `<timeout then retry test>`
- `<concurrent duplicate test>`
- `<message redelivery test>`
