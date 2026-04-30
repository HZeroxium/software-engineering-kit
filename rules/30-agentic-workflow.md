# Agentic Workflow

## Default Workflow for Non-Trivial Work

Use this workflow for non-trivial coding, debugging, review, documentation, migration, or architecture tasks:

1. Explore read-only.
2. Summarize findings and assumptions.
3. Ask targeted questions if requirements are ambiguous or risk is high.
4. Propose an implementation plan with affected files, risks, tests, and rollback considerations.
5. Implement small, focused changes only after scope is clear.
6. Verify with the narrowest useful checks first, then broader checks.
7. Summarize diff, tests run, tests not run, residual risks, and next steps.

For simple low-risk tasks, a shorter flow is acceptable, but still preserve correctness and validation discipline.

## Explore Read-Only

Before editing:

- Inspect relevant files.
- Inspect current diffs when applicable.
- Find existing patterns.
- Identify ownership boundaries.
- Identify tests and validation commands from the repo.
- Identify risky areas such as auth, data mutation, migrations, infrastructure, secrets, or generated code.

Do not start with broad rewrites.

## Findings and Assumptions

After exploration, summarize:

- Confirmed facts
- Assumptions
- Relevant existing patterns
- Missing context
- Risk level
- Proposed scope

Keep this summary concise and actionable.

## Clarifying Questions

Ask targeted questions before implementation when:

- Requirements are ambiguous.
- The task has security impact.
- The task may affect production behavior.
- There are multiple valid designs with different trade-offs.
- Public APIs, schemas, migrations, or compatibility are involved.
- The user’s requested change conflicts with existing tests, docs, or code.
- The blast radius is unclear.

Avoid asking questions that can be answered by inspecting the repository.

## Planning

For meaningful changes, propose a plan that includes:

- Affected files or modules
- Intended behavior change
- Minimal implementation steps
- Tests to add or update
- Validation commands to run, discovered from the repo
- Risks and edge cases
- Rollback considerations

Keep plans practical and scoped.

## Implementation

When implementing:

- Make minimal diffs.
- Follow existing project style.
- Preserve public behavior unless change is intentional.
- Avoid unrelated refactors.
- Avoid broad formatting.
- Avoid unapproved dependency upgrades.
- Keep changes reviewable.
- Update tests with behavior changes.
- Update docs when public behavior, commands, APIs, or workflows change.

## High-Risk Edits

Require approval before high-risk edits involving:

- Auth/security
- Secrets
- Database migrations
- Data deletion or backfills
- CI/CD
- Infrastructure
- Production configs
- Dependency upgrades
- Public API or schema changes
- Broad rewrites
- Destructive commands

If approval is not available, stop at a plan or patch proposal.

## Verification

Verify with the narrowest useful check first:

- Targeted unit test
- Targeted integration test
- Type check for affected package
- Lint for affected files
- Build for affected module
- Static analysis for affected scope

Then broaden when appropriate:

- Full module test suite
- Full package build
- Full repository CI-equivalent check

Do not invent verification commands. Discover them from the repo.

## Final Summary

At the end of non-trivial work, summarize:

- What changed
- Why it changed
- Files touched
- Tests run
- Tests not run
- Validation result
- Residual risks
- Follow-up recommendations

Be explicit when validation was not possible.
