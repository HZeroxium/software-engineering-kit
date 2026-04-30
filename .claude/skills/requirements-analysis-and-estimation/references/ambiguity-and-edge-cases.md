# Ambiguity and Edge Cases

## Common Ambiguity Patterns

Look for unclear statements such as:

- “User can manage X.”
- “System should validate data.”
- “Make it faster.”
- “Improve UX.”
- “Support admin.”
- “Sync with external system.”
- “Handle errors.”
- “Send notification.”
- “Use the latest data.”
- “Allow retry.”
- “Should be secure.”

For each ambiguous statement, ask:

- Who performs the action?
- What exact action is allowed?
- What input is valid?
- What input is invalid?
- What output is expected?
- What state changes?
- What is persisted?
- What is visible to the user?
- What errors are shown?
- What is logged or measured?
- What happens on retry?
- What happens under concurrency?

## Edge Case Categories

### Input

- Missing input
- Null input
- Empty string/list
- Invalid format
- Too long
- Too short
- Unsupported enum/status
- Duplicate input
- Conflicting input

### Data

- Record not found
- Soft-deleted record
- Stale data
- Duplicate record
- Partial data
- Corrupted data
- Migration state
- Backward-compatible old data

### Permissions

- Anonymous user
- Authenticated but unauthorized user
- Expired session/token
- Role changed during operation
- Cross-tenant access
- Admin vs regular user

### Concurrency

- Double submit
- Retry after timeout
- Two users update same record
- Idempotency key reuse
- Race between validation and write
- Lock contention

### Integration

- Upstream timeout
- Downstream rejection
- Partial success
- Retryable failure
- Non-retryable failure
- Rate limit
- Contract mismatch
- Version mismatch

### Operations

- Deployment during in-flight requests
- Feature flag off/on
- Rollback after partial rollout
- Missing config
- Secret unavailable
- High load
- Observability gap
