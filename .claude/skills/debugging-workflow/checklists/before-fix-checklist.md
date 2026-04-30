# Before Fix Checklist

Use before editing code for a bug fix.

## Root Cause Confidence

- [ ] Root cause is confirmed, or uncertainty is clearly stated.
- [ ] Evidence supports the proposed fix.
- [ ] The fix addresses the cause, not only the symptom.
- [ ] A regression test can be described.

## Scope

- [ ] Affected files/modules are identified.
- [ ] Public API impact is understood.
- [ ] Data impact is understood.
- [ ] Security impact is understood.
- [ ] Compatibility impact is understood.

## Safety

- [ ] No migration is required, or approval is requested.
- [ ] No auth/security change is required, or approval is requested.
- [ ] No production config change is required, or approval is requested.
- [ ] No dependency upgrade is required, or approval is requested.
- [ ] No destructive command is required, or approval is requested.
- [ ] No secret handling change is required, or approval is requested.

## Validation

- [ ] Narrow validation command is discovered from repo.
- [ ] Regression test plan exists.
- [ ] Broader validation is identified if needed.
- [ ] Rollback path is understood for risky changes.
