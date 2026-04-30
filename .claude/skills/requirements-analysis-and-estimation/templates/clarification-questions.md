# Clarification Questions

## Blocking Questions

Questions that must be answered before implementation:

1.
2.
3.

## Product / Business Questions

- Who is the target user?
- What problem are we solving?
- What user-visible behavior should change?
- What should remain unchanged?
- What is the success metric?
- What is the release priority?

## Functional Questions

- What are the valid inputs?
- What are the invalid inputs?
- What are the expected outputs?
- What states can the entity move through?
- What actions are allowed?
- What actions are prohibited?
- What happens on duplicate requests?
- What happens when data is missing?

## Non-Functional Questions

- What latency or throughput is expected?
- What reliability level is required?
- What data retention rules apply?
- What audit or traceability is required?
- What security or permission constraints apply?
- What compatibility constraints apply?

## Integration Questions

- Which systems are involved?
- Which API owns the source of truth?
- What happens if an upstream dependency fails?
- What happens if a downstream dependency rejects the request?
- Is retry safe?
- Is idempotency required?

## Data Questions

- What data is created?
- What data is updated?
- What data is deleted?
- Is migration required?
- Is rollback required?
- Are there privacy or sensitive-data concerns?

## Testing Questions

- What is the minimum acceptance test?
- What regression risks matter most?
- What existing tests cover similar behavior?
- What manual QA is required?
