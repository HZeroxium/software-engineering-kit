# Transaction and Consistency Thinking

## Purpose

Use this reference when a backend feature reads/writes data, triggers side effects, or crosses service boundaries.

## Core Questions

- What must be atomic?
- What can be eventually consistent?
- What state is visible before side effects complete?
- What happens if the process crashes after commit?
- What happens if an external call succeeds but local persistence fails?
- What happens if a message is delivered twice?
- What happens under retry?

## Transaction Boundary Rules

Prefer transaction boundaries that:

- Protect critical invariants.
- Are short and local.
- Avoid external network calls inside the transaction when possible.
- Avoid long-running locks.
- Make side effects recoverable.
- Keep retry behavior explicit.

## Common Patterns

### Local Transaction

Use when one database or transactional resource owns the state change.

### Outbox

Use when local state changes must reliably publish an event/message.

### Inbox / Deduplication

Use when message consumers must handle duplicate delivery.

### Saga

Use when a business workflow spans multiple services and needs compensation.

### Idempotency Key

Use when clients or workers may retry operations.

## Failure Matrix

| Failure Point               | Example                | Design Response               |
| --------------------------- | ---------------------- | ----------------------------- |
| Before transaction commit   | validation fails       | return error, no side effects |
| After commit before publish | process crashes        | outbox recovery               |
| External provider timeout   | payment unclear        | idempotency + reconciliation  |
| Message duplicated          | at-least-once delivery | consumer deduplication        |
| Retry after success         | client timeout         | return previous result        |

## Anti-Patterns

- Assuming exactly-once delivery.
- Retrying non-idempotent writes.
- Calling slow external services inside DB transactions.
- Relying only on application code for critical uniqueness.
- Emitting events before state commits.
