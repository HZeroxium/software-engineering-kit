# Before Edit Checklist

Use before modifying files.

## Scope

- [ ] I understand the user request.
- [ ] I know what is in scope.
- [ ] I know what is out of scope.
- [ ] I have identified assumptions.
- [ ] I have identified missing context.

## Repo Context

- [ ] I inspected relevant files.
- [ ] I inspected existing patterns.
- [ ] I checked current diffs if relevant.
- [ ] I identified relevant tests.
- [ ] I identified relevant configs.
- [ ] I identified build/test commands from repo evidence if needed.

## Safety

- [ ] The change is not destructive.
- [ ] The change does not expose secrets.
- [ ] The change does not mutate production systems.
- [ ] The change does not require migration approval.
- [ ] The change does not require auth/security approval.
- [ ] The change does not require CI/CD or infrastructure approval.
- [ ] If high-risk, explicit approval has been requested.

## Implementation

- [ ] Planned diff is small and focused.
- [ ] Existing style will be preserved.
- [ ] Tests will be added or updated when behavior changes.
- [ ] Docs will be updated when public behavior changes.
- [ ] Rollback path is understood for risky changes.
