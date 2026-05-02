---
purpose: Correctness, domain rule, state, contract, and data consistency review checks
load-when: Reviewing behavior, business logic, API contracts, state transitions, or data writes
tier: domain
see-also: []
---

# Functional Correctness and Business Logic Review

## Core Questions

- Does the code implement the requested behavior?
- Does it preserve existing behavior that should not change?
- Are domain rules explicit and correctly applied?
- Are state transitions valid?
- Are invariants preserved?
- Are edge cases handled?
- Are errors handled in the expected contract?
- Are API inputs and outputs compatible?
- Are database writes transactionally correct?
- Are partial updates possible?
- Are null, empty, missing, duplicate, and invalid states handled?

## Backend Review Focus

For Java/Spring or backend services, inspect:

- Controller/API contract.
- Service layer business rules.
- Transaction boundaries.
- Repository/query behavior.
- DTO/entity mapping.
- Validation annotations and manual validation.
- Exception handling and error response mapping.
- Idempotency and retry safety.
- Soft delete and status handling.
- Multi-tenant or owner checks.
- Backward compatibility.

## Data Consistency

Look for:

- Writes outside transaction boundaries.
- Missing optimistic/pessimistic locking when needed.
- Duplicate creation under retry or concurrency.
- Lost update risk.
- Inconsistent derived fields.
- Incomplete rollback behavior.
- Event emitted before transaction commits.
- Cache updated before source-of-truth commit.
- Read-after-write assumptions.
- Stale data assumptions.

## Edge Cases

Check:

- Null input.
- Empty collection.
- Missing record.
- Duplicate request.
- Invalid status.
- Unauthorized actor.
- Cross-tenant access.
- Deleted/disabled entity.
- Boundary numeric values.
- Time zone and time boundary.
- Retry after timeout.
- Partial dependency failure.

## Review Output

For each issue:

- State the violated requirement, rule, or invariant.
- Show the failure scenario.
- Explain production impact.
- Suggest the smallest fix.
- Suggest a regression test.
