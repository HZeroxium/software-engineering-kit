# Review Priority Model

Review in this priority order.

## 1. Functional Correctness and Business Logic

Most important because code that compiles but implements the wrong behavior is still a production defect.

Look for:

- Requirement mismatch.
- Broken domain rule.
- Incorrect data flow.
- Incorrect transaction behavior.
- Invalid state transition.
- Broken invariant.
- Missing edge case.
- Incorrect error handling.
- Compatibility regression.

## 2. Security, Privacy, Abuse Risk, and Reliability

Security and privacy issues can create severe blast radius even when the feature appears to work.

Look for:

- Broken authentication.
- Broken authorization.
- Input validation gaps.
- Injection risk.
- Secret exposure.
- Sensitive logging.
- Unsafe crypto.
- Dependency risk.
- Security misconfiguration.
- Abuse cases.
- Privacy leakage.
- Reliability gaps that can cause user-visible incidents.

## 3. Concurrency and Failure Handling

Distributed systems and backend services often fail under concurrency, retries, partial failures, and timeouts.

Look for:

- Race conditions.
- Missing idempotency.
- Unsafe retries.
- Retry storms.
- Timeout gaps.
- Partial failure gaps.
- Transaction boundary mistakes.
- Resource lifecycle leaks.
- Thread-safety issues.
- Connection leaks.

## 4. Performance and Scalability

Performance issues often hide until realistic data volume or traffic.

Look for:

- N+1 queries.
- Inefficient loops.
- Blocking calls in async/reactive paths.
- Lock contention.
- Excessive memory allocation.
- Missing pagination.
- Missing batching.
- Query/index risk.
- High-cardinality metrics.
- Unbounded data loading.

## 5. Maintainability, Architecture, Tests, and Observability

These determine long-term cost and operability.

Look for:

- Poor boundaries.
- Unclear ownership.
- Excessive coupling.
- Duplication.
- Overly broad abstraction.
- Missing tests.
- Brittle tests.
- Weak assertions.
- Missing logs/metrics/traces.
- Unclear failure diagnostics.

## Severity Definitions

### Blocking

Must fix before merge.

Examples:

- Incorrect behavior.
- Security vulnerability.
- Data loss or corruption risk.
- Broken authorization.
- Unsafe migration.
- Race condition with production impact.
- Missing critical validation.
- Build or tests fail.
- Public API break without migration plan.

### Important

Should usually fix before merge.

Examples:

- Missing meaningful tests.
- Ambiguous failure handling.
- Performance risk.
- Observability gap.
- Maintainability risk in touched area.
- Incomplete edge case handling.
- Weak input validation with limited impact.

### Optional

May fix later.

Examples:

- Naming improvement.
- Minor simplification.
- Small documentation improvement.
- Non-critical refactor.
- Low-risk readability issue.
