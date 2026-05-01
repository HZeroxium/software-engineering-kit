# Backend Implementation Plan

## Task

`<implementation task>`

## Design Source

- **Design available:** `<yes/no>`
- **Source:** `<backend-feature-design / user description / issue / code>`
- **Design gaps:** `<gaps>`

## Read-Only Exploration Summary

| Area                | Evidence                | Notes     |
| ------------------- | ----------------------- | --------- |
| Affected module     | `<files/dirs>`          | `<notes>` |
| Existing pattern    | `<files/classes/tests>` | `<notes>` |
| Internal libraries  | `<imports/usages>`      | `<notes>` |
| Validation commands | `<evidence>`            | `<notes>` |

## Affected Files / Modules

| File / Module | Change Type           | Reason     |
| ------------- | --------------------- | ---------- |
| `<path>`      | `<add/edit/test/doc>` | `<reason>` |

## Implementation Strategy

1. `<step>`
2. `<step>`
3. `<step>`

## Minimal Diff Strategy

- Keep changes focused around `<module/use case>`.
- Preserve public contracts unless explicitly changing them.
- Reuse existing repository conventions.
- Add or update tests near changed behavior.
- Avoid broad formatting-only changes.

## Test Plan

| Test     | Type                               | Purpose     |
| -------- | ---------------------------------- | ----------- |
| `<test>` | `<unit/integration/contract/etc.>` | `<purpose>` |

## Validation Commands

| Command     | Evidence           |       Safe to Run? |
| ----------- | ------------------ | -----------------: |
| `<command>` | `<file/script/CI>` | `<yes/no/unknown>` |

## Risk Gates

- [ ] Migration required.
- [ ] Auth/security change required.
- [ ] Production config affected.
- [ ] CI/CD affected.
- [ ] Dependency upgrade required.
- [ ] Generated code affected.
- [ ] Secret handling involved.
- [ ] External system write involved.

## Exit Criteria

- [ ] Implementation matches design.
- [ ] Tests added/updated.
- [ ] Validation command run or documented.
- [ ] Residual risks listed.
