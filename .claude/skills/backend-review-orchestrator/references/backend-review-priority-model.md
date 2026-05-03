---
purpose: Blocking, Important, and Optional severity thresholds with examples for backend review findings
load-when: Assigning severity to a finding or calibrating the overall risk level of a review
tier: foundational
see-also:
  - backend-production-risk-model.md
---

# Backend Review Priority Model

## Blocking

A finding is Blocking if it can cause:

- Security vulnerability.
- Broken authorization.
- Cross-tenant data exposure.
- Data loss or corruption.
- Unsafe migration.
- Public contract break.
- Production outage.
- Severe retry/idempotency bug.
- Unbounded resource exhaustion.
- Missing validation for high-risk behavior.
- Secret leakage.
- AI tool side effect without approval.

## Important

A finding is Important if it can cause:

- Meaningful bug under edge cases.
- Incomplete error handling.
- Missing tests for important behavior.
- Maintainability risk in core path.
- Observability gap for production debugging.
- Performance risk under expected load.
- Incomplete failure handling.
- Ambiguous ownership or module boundary.

## Optional

A finding is Optional if it improves:

- Naming.
- Readability.
- Minor structure.
- Non-critical test cleanup.
- Documentation clarity.
- Local refactoring.
- Minor observability polish.

## Rule

Do not inflate style preferences into Blocking findings. Severity must be tied to realistic failure mode and impact.
