---
purpose: Step-by-step workflow for explore, plan, implement, verify, summarize with implementation-specific guidance
load-when: Starting any implementation task or when the workflow steps need clarification
tier: foundational
see-also:
  - exit-criteria.md
  - rollback-thinking.md
---

# Explore → Plan → Implement → Verify

## 1. Explore Read-Only

Goal: understand before changing.

### Task Risk Tier

Before starting, classify the task:

| Tier   | Characteristics                                                         | Action                          |
| ------ | ----------------------------------------------------------------------- | ------------------------------- |
| Low    | Single file, no public API change, no data mutation                     | Proceed directly                |
| Medium | Multi-file, test coverage needed, config change possible                | Summarize findings first        |
| High   | Migration, auth/security, CI/CD, production config, or broad rewrite   | Require explicit approval       |

Inspect:

- User request.
- Relevant files.
- Current diffs.
- Existing patterns.
- Tests.
- Configs.
- Build files.
- Scripts.
- Docs.
- CI config.
- Logs or stack traces.
- Acceptance criteria.

Avoid edits during exploration unless the user explicitly requested a trivial change.

## 2. Summarize Findings

Summarize:

- Confirmed facts.
- Assumptions.
- Missing context.
- Existing patterns.
- Risk level.
- Likely affected files.

## 3. Ask Targeted Questions

Ask questions when:

- Requirements are ambiguous.
- Risk is high.
- Public APIs or schemas may change.
- Migrations are involved.
- Auth/security is involved.
- Production behavior may change.
- Rollback path is unclear.

Do not ask questions that can be answered by inspecting the repo.

## 4. Plan

Plan should include:

- Scope.
- Affected files.
- Implementation steps.
- Tests.
- Validation commands discovered from repo.
- Risks.
- Rollback.
- Approval needs.

## 5. Implement

Implementation should be:

- Small.
- Focused.
- Reviewable.
- Consistent with existing style.
- Minimal in blast radius.
- Covered by tests where practical.

Avoid:

- Broad rewrites.
- Unrelated formatting.
- Unapproved dependency upgrades.
- Unnecessary architecture changes.
- Touching generated files unless expected.

## 6. Verify

Start narrow:

- Targeted test.
- Type check for affected module.
- Lint for affected files.
- Compile affected module.

Then broaden when justified:

- Full package tests.
- Full build.
- CI-equivalent command.

Do not invent commands.

## 7. Summarize

Final summary should include:

- What changed.
- Files touched.
- Validation run.
- Validation not run.
- Risks.
- Residual issues.
- Next steps.
