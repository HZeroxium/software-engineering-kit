---
purpose: Quality bar checklist for reviewing requirements before implementation planning
load-when: Reviewing or finalizing a set of requirements
---

# Requirement Quality Checklist

Use this checklist to review requirements before implementation planning.

## Clarity

- Requirement uses concrete language.
- Requirement avoids vague words such as “fast”, “easy”, “properly”, “intuitive”, or “secure” without measurable meaning.
- Actor, action, input, output, and result are identifiable.
- Required behavior and prohibited behavior are both clear.

## Testability

- Requirement can be verified by test, review, log, metric, or manual scenario.
- Acceptance criteria are observable.
- Error behavior is specified.
- Permission behavior is specified when relevant.
- Empty, invalid, duplicate, and boundary cases are covered.

## Completeness

- Functional requirements are listed.
- Non-functional requirements are listed.
- Business rules are listed.
- Invariants are listed.
- Data impact is listed.
- API or UI impact is listed.
- Compatibility concerns are listed.
- Observability expectations are listed.

## Consistency

- Requirements do not conflict with each other.
- Requirements do not conflict with known current behavior unless the change is intentional.
- Terminology is consistent.
- Entity names and statuses are consistent.
- Priority is clear.

## Feasibility

- Technical constraints are known.
- Dependencies are known.
- Migration needs are known.
- Security implications are known.
- Operational impact is known.
- Scope is realistic for the target release.

## Risk

Call out risk when requirements involve:

- Authentication or authorization.
- Payments or financial data.
- Customer data.
- Data deletion or migration.
- Production configs.
- CI/CD or infrastructure.
- Backward compatibility.
- Concurrency or idempotency.
- External integrations.
- High traffic or strict latency.
