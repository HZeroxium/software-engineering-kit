# Use-Case Orchestration

## Purpose

Use-case orchestration coordinates backend behavior around user or business intent.

## Orchestration Responsibilities

- Validate use-case preconditions.
- Load required state.
- Call domain behavior.
- Manage transaction boundary.
- Invoke persistence ports/adapters.
- Schedule or emit side effects safely.
- Map domain/application result to interface response.

## Questions

- Is this a command or query?
- What state is read and written?
- What must be atomic?
- Which side effects happen after commit?
- What happens on partial failure?
- What tests prove the workflow?

## Smells

- Controller handles workflow.
- Repository performs business decisions.
- Use case calls many unrelated services.
- Side effects occur before durable state.
- No clear owner for transaction boundary.
