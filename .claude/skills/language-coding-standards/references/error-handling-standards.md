# Error Handling Standards

## Goals

Good error handling should:

- Preserve correctness.
- Avoid leaking sensitive data.
- Help users recover when possible.
- Help operators diagnose failures.
- Keep domain, application, and infrastructure errors distinguishable.

## Error Categories

- Validation error.
- Authentication error.
- Authorization error.
- Not found.
- Conflict.
- Rate limit.
- Timeout.
- Dependency failure.
- Data integrity error.
- Internal error.
- Cancellation.
- Retryable failure.
- Non-retryable failure.

## Boundary Rules

At system boundaries:

- Validate input.
- Convert internal exceptions to stable external error contracts.
- Redact sensitive details.
- Preserve correlation/request identifiers.
- Use consistent status/error codes.

Inside application logic:

- Use domain-specific errors where meaningful.
- Preserve cause when wrapping.
- Avoid swallowing errors.
- Avoid broad catch blocks unless adding useful handling.

## Retry Classification

Before retrying, decide:

- Is the failure transient?
- Is the operation idempotent?
- Is there a timeout?
- Are retries bounded?
- Is backoff used?
- Could retry amplify an outage?

## Logging Errors

Log:

- Safe entity IDs.
- Error category.
- Dependency name.
- Operation name.
- Correlation ID.
- Retry count if relevant.

Do not log:

- Secrets.
- Tokens.
- Passwords.
- Full sensitive payloads.
- Private customer data.
