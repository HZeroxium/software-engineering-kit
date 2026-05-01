# Backend Design Review Before Implementation

## Must Be Clear Before Implementation

- [ ] What behavior is being added or changed.
- [ ] Which public/internal contracts change.
- [ ] Which modules/files are likely affected.
- [ ] Which data is read/written.
- [ ] Which authorization rules apply.
- [ ] Which side effects occur.
- [ ] Which operations must be idempotent.
- [ ] Which validations are required.
- [ ] Which failure modes are acceptable.
- [ ] Which tests are expected.
- [ ] Which validation commands should be run.

## Escalate Before Implementation If

- [ ] Auth/security behavior is unclear.
- [ ] Object-level authorization is unclear.
- [ ] Tenant isolation is unclear.
- [ ] Migration is needed.
- [ ] Production configuration is affected.
- [ ] CI/CD or infrastructure is affected.
- [ ] Internal library behavior is unknown.
- [ ] Public API compatibility is unclear.
- [ ] External provider contract is unclear.
- [ ] Required tests cannot be identified.

## Implementation Handoff Ready

- [ ] Design summary exists.
- [ ] Risk register exists.
- [ ] Test strategy exists.
- [ ] Open questions are acceptable or resolved.
- [ ] Human approval gates are documented.
