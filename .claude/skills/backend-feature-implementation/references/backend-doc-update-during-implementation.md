---
purpose: Decision criteria for when to update documentation during implementation; docs to consider; what to avoid
load-when: Implementation changes a public API contract, error model, config requirements, operational behavior, or developer workflow
tier: scenario
see-also: []
---

# Backend Documentation Update During Implementation

## Principle

Update documentation only when the implementation changes behavior, contracts, operations, or developer workflow.

## Docs to Consider

- API docs.
- README.
- Developer setup.
- Config examples.
- Runbooks.
- Architecture decision records.
- `docs/ai/repo-map.md` if present and relevant.
- Contract/schema docs.
- Migration notes.
- Release notes.

## Update Docs When

- API contract changes.
- Error model changes.
- Config requirements change.
- Validation commands change.
- Operational behavior changes.
- New metric/log/alert/runbook is added.
- Migration steps are required.
- AI prompt/model/evaluation behavior changes.

## Avoid

- Creating docs as a substitute for tests.
- Updating docs based on speculation.
- Duplicating stale implementation details.
- Editing repo-level AI artifacts without user request if outside task scope.
