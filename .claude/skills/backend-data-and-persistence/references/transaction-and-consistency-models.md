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
