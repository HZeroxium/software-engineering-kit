# Module Boundary Review

## Scope

`<module/service/package boundary>`

## Boundary Summary

| Module     | Responsibility     | Public Surface          | Internal Details |
| ---------- | ------------------ | ----------------------- | ---------------- |
| `<module>` | `<responsibility>` | `<APIs/classes/events>` | `<internal>`     |

## Dependency Review

| From       | To         |   Allowed? | Reason     |
| ---------- | ---------- | ---------: | ---------- |
| `<module>` | `<module>` | `<yes/no>` | `<reason>` |

## Coupling Risks

- `<risk>`
- `<risk>`

## Boundary Smells

- [ ] Cyclic dependencies.
- [ ] Common module as dumping ground.
- [ ] Domain depends on infrastructure.
- [ ] Transport layer owns business logic.
- [ ] Internal classes exposed publicly.
- [ ] Shared mutable state.
- [ ] Testability blocked by hard dependencies.

## Recommendation

`<minimal boundary improvement>`

## Validation

- `<compile/module test/static analysis/review>`
