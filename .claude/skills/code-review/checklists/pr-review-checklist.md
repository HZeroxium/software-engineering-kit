---
purpose: Checklist for complete PR, diff, or merge-readiness review
load-when: Reviewing a complete PR, broad diff, or merge readiness
---

# PR Review Checklist

## Context

- [ ] I understand the requirement or ticket.
- [ ] I know what behavior should change.
- [ ] I know what behavior should not change.
- [ ] I inspected relevant files, tests, and configs.
- [ ] I separated facts from assumptions.

## Correctness

- [ ] Domain rules are preserved.
- [ ] State transitions are valid.
- [ ] Data flow is correct.
- [ ] Error behavior is correct.
- [ ] Edge cases are handled.
- [ ] Backward compatibility is considered.

## Security and Privacy

- [ ] AuthN/AuthZ is correct.
- [ ] Input validation is adequate.
- [ ] No injection risk is introduced.
- [ ] Secrets are not exposed.
- [ ] Sensitive data is not logged.
- [ ] Cross-tenant/user data leakage is prevented.
- [ ] Abuse cases are considered.

## Concurrency and Failure

- [ ] Retries are safe.
- [ ] Timeouts are considered.
- [ ] Idempotency is considered.
- [ ] Transactions are correct.
- [ ] Partial failures are handled.
- [ ] Resources are closed.
- [ ] Race conditions are considered.

## Performance and Scalability

- [ ] No obvious N+1 query.
- [ ] Pagination/limits exist where needed.
- [ ] Queries are index-friendly.
- [ ] No unbounded memory growth.
- [ ] Blocking calls are not in unsafe paths.
- [ ] Metrics avoid high cardinality.

## Tests and Observability

- [ ] Meaningful tests exist.
- [ ] Regression tests exist for bug fixes.
- [ ] Tests are deterministic.
- [ ] Logs/metrics/traces are considered.
- [ ] Validation commands are discovered, not invented.

## Final Review

- [ ] Findings are severity-ranked.
- [ ] Minimal fixes are suggested.
- [ ] Remaining risks are stated.
