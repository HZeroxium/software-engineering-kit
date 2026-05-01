# Outbox / Inbox Analysis

## Workflow

`<workflow or integration>`

## Outbox Need

- **Needed:** `<yes/no/unknown>`
- **Reason:** `<state change must reliably publish event/message>`

## Inbox Need

- **Needed:** `<yes/no/unknown>`
- **Reason:** `<consumer must handle duplicate delivery>`

## Local State Change

| State Change | Must Publish Event? | Failure Risk |
| ------------ | ------------------: | ------------ |
| `<change>`   |          `<yes/no>` | `<risk>`     |

## Outbox Design

| Concern                 | Decision                                       |
| ----------------------- | ---------------------------------------------- |
| Outbox storage          | `<table/collection/internal mechanism>`        |
| Publish trigger         | `<poller/transaction hook/job/internal infra>` |
| Retry policy            | `<policy>`                                     |
| Ordering requirement    | `<requirement>`                                |
| Poison message handling | `<policy>`                                     |

## Inbox / Dedup Design

| Concern            | Decision                       |
| ------------------ | ------------------------------ |
| Message ID         | `<field>`                      |
| Dedup storage      | `<table/collection/cache>`     |
| Dedup window       | `<duration>`                   |
| Duplicate behavior | `<ignore/replay result/no-op>` |

## Failure Matrix

| Failure                        | Result Without Pattern | Mitigation            |
| ------------------------------ | ---------------------- | --------------------- |
| Commit succeeds, publish fails | `<impact>`             | `<outbox/recovery>`   |
| Message delivered twice        | `<impact>`             | `<inbox/dedup>`       |
| Consumer crashes mid-process   | `<impact>`             | `<retry/idempotency>` |

## Validation

- `<outbox recovery test>`
- `<duplicate delivery test>`
- `<poison message test>`
