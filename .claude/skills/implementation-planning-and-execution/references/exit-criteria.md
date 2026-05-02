---
purpose: Readiness criteria for implementation tasks — functional, quality, validation, documentation, observability, and security gates
load-when: Deciding whether a completed implementation is ready for final summary or needs further validation
tier: domain
see-also:
  - explore-plan-implement-verify.md
---

# Exit Criteria

A task is ready for final summary when the following are true or explicitly documented as not possible.

## Functional Readiness

- Requested behavior is implemented.
- Acceptance criteria are addressed.
- Existing behavior is preserved unless intentionally changed.
- Edge cases are handled or documented.
- Error behavior is reasonable.

## Code Quality

- Diff is minimal and reviewable.
- Existing style is preserved.
- Names are clear.
- No unrelated refactors.
- No unapproved dependency upgrades.
- No invented APIs or framework behavior.
- No secrets or sensitive data added.

## Validation

- Relevant tests pass.
- Build passes when available and relevant.
- Typecheck passes when available and relevant.
- Lint/static analysis passes when available and relevant.
- Manual checks are documented when automated checks are unavailable.
- Tests not run are listed with reasons.

## Documentation

- Public behavior changes are documented.
- API changes are documented.
- Command changes are documented.
- Migration or rollback notes are documented when relevant.
- Stale docs are updated or flagged.

## Observability

Consider observability when behavior or failure modes change:

- Logs are useful but not noisy.
- Metrics avoid high cardinality.
- Errors are diagnosable.
- Alerts/dashboards are considered when production behavior changes.

## Security and Review

Manual review required for:

- Auth/security.
- Secrets.
- Data access.
- Database migrations.
- CI/CD.
- Infrastructure.
- Production configs.
- Public API/schema changes.
- Destructive operations.

### Smart Escalation Heuristics

Escalate immediately (do not attempt a fix) when:

- Failure cause is unclear after one fix attempt.
- The fix requires modifying unrelated modules.
- A migration or data change is discovered mid-implementation.
- A security-sensitive invariant may be violated.

## Final Reporting

Final answer includes:

- Summary.
- Files changed.
- Tests run.
- Tests not run.
- Residual risks.
- Next steps.
