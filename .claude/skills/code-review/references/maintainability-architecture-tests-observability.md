---
purpose: Maintainability, architecture, tests, and observability review checks
load-when: Reviewing structure, boundaries, test coverage, diagnostics, logs, metrics, or traces
tier: domain
see-also: []
---

# Maintainability, Architecture, Tests, and Observability Review

## Maintainability

Check:

- Code is readable.
- Names reveal intent.
- Logic is not duplicated unnecessarily.
- Functions/classes have clear responsibilities.
- Error handling is explicit.
- Comments explain why, not obvious what.
- Complex conditionals are understandable.
- Public APIs are stable and documented.

## Architecture

Check:

- Boundaries are respected.
- Domain logic is not misplaced.
- Controllers do not contain business logic.
- Persistence details do not leak unnecessarily.
- Dependency direction is reasonable.
- Abstractions are justified.
- Coupling is not increased without benefit.
- Compatibility is preserved.

## Tests

Check:

- Changed behavior has tests.
- Tests cover success, failure, edge, and permission cases.
- Tests are deterministic.
- Tests avoid brittle implementation details.
- Assertions verify meaningful outcomes.
- Mocks do not hide integration risk.
- Regression tests capture the bug or risk.
- Test names explain behavior.

## Observability

Check:

- Important failures are diagnosable.
- Logs are useful but not noisy.
- Sensitive data is redacted.
- Metrics are low-cardinality and actionable.
- Traces preserve cross-service context where relevant.
- Error handling includes enough context for debugging.
- Alerts or dashboards are considered for production behavior changes.

## Review Output

For each finding:

- Explain maintainability or operational impact.
- Avoid style-only nitpicks unless they affect readability or consistency.
- Prefer minimal changes near touched code.
