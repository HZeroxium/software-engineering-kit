# Data Consistency and Transactions

## Consistency Questions

- What is the source of truth?
- Which operation must be atomic?
- What can be eventually consistent?
- What happens on partial failure?
- What happens on retry?
- What happens under concurrency?
- What invariants must always hold?
- What can be reconciled later?

## Transaction Boundaries

Review:

- Where does the transaction start and end?
- Are reads and writes in the same transaction when needed?
- Are external calls inside transactions?
- Are events emitted before or after commit?
- Are caches updated safely?
- Are locks needed?
- Is isolation level adequate?
- Is rollback behavior correct?

## Common Risks

- Lost update.
- Duplicate insert.
- Partial commit.
- Event published for rolled-back transaction.
- Cache inconsistency.
- Read stale data as if fresh.
- Retry creates duplicate side effects.
- Long transaction holds locks.
- External call inside transaction causes contention.

## Patterns

### Single Transaction

Best for one service and one database boundary.

### Outbox

Use when state change and event publication must be coordinated.

### Saga / Process Manager

Use for long-running workflows across services.

### Idempotency Key

Use when clients, queues, or jobs may retry.

### Optimistic Locking

Use when concurrent updates are possible and conflict detection is acceptable.

## Validation

- Unit tests for invariants.
- Integration tests for transaction behavior.
- Concurrency tests for duplicate/lost update risks.
- Contract tests for events/APIs.
- Observability for retries, failures, and reconciliation.
