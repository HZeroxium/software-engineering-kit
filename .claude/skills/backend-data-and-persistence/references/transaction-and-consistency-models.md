---
purpose: Consistency model vocabulary, transaction smell detection, outbox pattern, idempotency keys, saga
load-when: Reviewing transaction boundaries, consistency requirements, or distributed write coordination
tier: foundational
see-also:
  - migration-strategy.md
  - caching-strategies.md
---

# Transaction and Consistency Models

## Purpose

Choose consistency guarantees that match business requirements.

## Models

- Strong consistency.
- Read-your-writes.
- Eventual consistency.
- Causal consistency.
- Best-effort async update.
- Reconciliation-based consistency.

## Questions

- What must be atomic?
- What can be stale?
- What is the user impact of stale data?
- Can conflicts occur?
- How are conflicts resolved?
- What happens under retry or crash?

## Transaction Smells

- Long transaction with external calls.
- Critical check done outside transaction.
- No concurrency control.
- Lost update possible.
- Side effect committed but data rolled back.
- Data committed but event lost.

## Outbox Pattern

Use when a DB write and an event/message must succeed or fail atomically.

Pattern:
1. Write domain state + outbox record in one local transaction.
2. Relay process reads outbox and publishes the event.
3. Mark outbox record as published after confirmed delivery.

Risks:
- Relay process down: events delay, not lost.
- Duplicate delivery possible: consumer must be idempotent.
- Outbox table growth: needs archival or cleanup policy.

## Idempotency Keys

Use to make state-changing operations safe to retry.

Pattern:
- Caller provides an idempotency key (UUID or client-generated).
- Server stores `unique(owner_id, idempotency_key)` to detect duplicates.
- Duplicate request returns previous result without re-executing.

Risks:
- Key must be scoped to owner to prevent cross-tenant collision.
- Key expiry policy needed for long-lived keys.
- Result of first execution must be stored for replay on duplicate.

## Saga Pattern

Use for multi-step operations that span multiple transactional boundaries.

Types:
- Choreography: each step publishes an event the next step listens to.
- Orchestration: a coordinator service issues commands to each participant.

Risks:
- No global rollback: compensating transactions must be designed explicitly.
- Partial failure visibility: saga state must be observable.
- Long saga duration: data may be inconsistent during execution.
- Compensating transactions may also fail: requires dead-letter handling.
