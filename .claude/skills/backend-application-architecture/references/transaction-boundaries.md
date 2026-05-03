---
purpose: Transaction boundary principles, atomicity review, side effect ordering, and retry behavior
load-when: Reviewing or designing transaction boundaries, atomicity, or post-commit side effects
tier: domain
see-also:
  - workflow-orchestration.md
---

# Transaction Boundaries

## Purpose

Define what must commit atomically and what must be recoverable.

## Principles

- Keep transactions short.
- Protect invariants inside transaction.
- Avoid network calls inside transactions unless explicitly justified.
- Emit side effects after durable state or through outbox-like patterns.
- Use database constraints for critical uniqueness.
- Make retry behavior explicit.

## Questions

- Which writes must succeed or fail together?
- Which side effects can happen after commit?
- Can the operation be retried?
- What happens if the process crashes after commit?
- Is concurrency controlled?

## Smells

- Transaction wraps slow external API call.
- Event published before commit.
- Critical invariant only checked in memory.
- No handling for concurrent duplicate requests.
- Framework transaction semantics assumed without evidence.
