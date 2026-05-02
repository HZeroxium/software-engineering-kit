---
purpose: Exception and stack trace analysis patterns
load-when: Debugging exceptions, caused-by chains, application frames, or line-number failures
tier: domain
see-also: []
---

# Stack Trace Analysis

## Reading Strategy

1. Identify the exception type.
2. Read the message.
3. Find the first application-owned frame.
4. Identify framework frames vs business code frames.
5. Trace call path upward.
6. Check caused-by chain.
7. Match line numbers to current code.
8. Compare with recent changes.

## What to Extract

- Exception type.
- Message.
- First failing application frame.
- Root cause chain.
- Input or state mentioned.
- Thread name.
- Test name or request path.
- Environment.
- Relevant config.

## Common Patterns

### Null Pointer / Undefined

Check:

- Missing validation.
- Optional value misuse.
- Unexpected missing dependency.
- Mapping missing field.
- Test fixture incomplete.

### Illegal State / Illegal Argument

Check:

- Invalid state transition.
- Missing precondition.
- Contract mismatch.
- Bad enum/status.
- Validation gap.

### Timeout

Check:

- Missing timeout.
- Slow dependency.
- Deadlock.
- Thread pool saturation.
- Query issue.
- Retry storm.
- Network/config issue.

### Constraint Violation

Check:

- Duplicate insert.
- Missing required field.
- Migration mismatch.
- Transaction ordering.
- Concurrent write.

### Class/Module Not Found

Check:

- Dependency mismatch.
- Build config.
- Runtime classpath.
- Packaging.
- Generated sources.

## Avoid

- Fixing the last frame blindly.
- Ignoring caused-by chain.
- Assuming framework frame is root cause.
- Ignoring recent changes.
- Ignoring environment differences.
