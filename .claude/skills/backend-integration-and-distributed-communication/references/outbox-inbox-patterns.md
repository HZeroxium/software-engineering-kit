# Outbox / Inbox Patterns

## Outbox

Use when a local state change must reliably publish a message/event.

Core idea:

```text
single local transaction:
  update business state
  insert outbox record

async publisher:
  publish outbox record
  mark sent
```

## Inbox

Use when a consumer must deduplicate messages.

Core idea:

```text
on message:
  check message ID in inbox
  if already processed: no-op
  else process and record processed ID
```

## Review Questions

- Can state commit without event publish?
- Can message publish happen twice?
- Can consumer process duplicate?
- How are outbox records retried?
- How are poison messages handled?
- Is ordering required?

## Failure Modes

- Lost event after DB commit.
- Duplicate event produces duplicate side effect.
- Outbox grows forever.
- Poison message blocks queue.
