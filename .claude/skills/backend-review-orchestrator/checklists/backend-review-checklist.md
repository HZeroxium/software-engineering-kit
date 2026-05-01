# Backend Review Checklist

## Correctness

- [ ] Behavior matches requirement.
- [ ] Domain rules enforced.
- [ ] State transitions valid.
- [ ] Edge cases handled.
- [ ] Error model consistent.

## API / Contract

- [ ] Contract is backward compatible or intentionally changed.
- [ ] Errors are stable and actionable.
- [ ] Pagination/filtering/idempotency handled where needed.
- [ ] Internal details not leaked.

## Architecture

- [ ] Responsibilities are placed correctly.
- [ ] Transaction boundaries are appropriate.
- [ ] Side effects are safe.
- [ ] Dependencies follow repo conventions.
- [ ] No unnecessary broad rewrite.

## Data

- [ ] Queries are correct.
- [ ] Constraints/indexes are considered.
- [ ] Migration is safe if present.
- [ ] Cache behavior is correct.
- [ ] Multi-tenancy is safe.

## Security

- [ ] Authentication checked where needed.
- [ ] Authorization checked where needed.
- [ ] Object-level access control checked.
- [ ] Secrets/sensitive data protected.
- [ ] Audit logging considered.

## Integration

- [ ] Timeouts defined.
- [ ] Retries safe.
- [ ] Duplicate handling considered.
- [ ] Contract compatibility checked.
- [ ] Failure behavior defined.

## Reliability / Performance / Observability

- [ ] Failure modes handled.
- [ ] Performance impact considered.
- [ ] Metrics/logs/traces added or preserved.
- [ ] Alerts/runbooks considered where needed.

## Testing

- [ ] Tests cover important behavior.
- [ ] Failure cases tested.
- [ ] Integration/contract tests added where needed.
- [ ] Validation evidence available.
