# Backend Quality Engineering

## Purpose

Backend quality engineering ensures the system is correct, testable, operable, secure, maintainable, and ready for production use.

## Quality Dimensions

- Correctness.
- Testability.
- Data integrity.
- Security and privacy.
- Reliability.
- Performance.
- Observability.
- Operability.
- Maintainability.
- Evolvability.
- Governance.
- AI quality where applicable.

## Backend Quality Questions

- What behavior must never regress?
- Which invariants must hold?
- Which contracts must remain compatible?
- Which failure modes are expected?
- Which signals prove the feature is healthy?
- What manual review is required?
- What residual risk remains?

## Quality Evidence

- Unit tests.
- Integration tests.
- Contract tests.
- Migration tests.
- Security tests.
- Evaluation datasets.
- Static analysis.
- Build/typecheck/lint.
- Logs/metrics/traces.
- Manual review.
- Audit logs.
- Architecture decision records.

## Review Smells

- “Works locally” without validation evidence.
- AI feature without evaluation.
- Security-sensitive feature without authorization tests.
- Data feature without migration or rollback plan.
- Production feature without observability.
- Compliance claim without evidence.
