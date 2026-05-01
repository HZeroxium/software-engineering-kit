# Backend Risk Gate Checklist

Ask for confirmation before proceeding if any item is true.

## Security

- [ ] AuthN/AuthZ behavior changes.
- [ ] Object-level authorization changes.
- [ ] Tenant isolation changes.
- [ ] Secrets or credentials handled.
- [ ] Sensitive data exposed, logged, or transmitted.

## Data

- [ ] Migration required.
- [ ] Data deletion required.
- [ ] Data retention behavior changes.
- [ ] Transaction behavior changes materially.
- [ ] Cache invalidation changes materially.

## Operations

- [ ] Production config changes.
- [ ] CI/CD changes.
- [ ] Infrastructure changes.
- [ ] Deployment behavior changes.
- [ ] Runtime controls changed.

## Dependencies and Generated Code

- [ ] Dependency upgrade required.
- [ ] Lockfile changes required.
- [ ] Generated code must be updated.
- [ ] Generator workflow is unclear.

## Scope

- [ ] Broad rewrite requested.
- [ ] Public contract breaking change.
- [ ] External system write required.
- [ ] Validation command may be destructive.
