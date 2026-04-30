# Agent Design Principles

## Good Agent Candidates

Create an Agent/Subagent when:

- The task benefits from separate context.
- The task involves large exploration.
- The agent can return a bounded summary.
- Tool access can be constrained.
- The role is stable and recurring.
- Independent review is useful.

## Poor Agent Candidates

Avoid an Agent when:

- A Skill is enough.
- The task is simple.
- The role is vague.
- The agent needs broad write access.
- Outputs overlap with existing agents.
- Coordination cost exceeds value.

## Default Boundary

Default to read-only for:

- Reviewers.
- Auditors.
- Researchers.
- Security reviewers.
- Documentation reviewers.

Grant write access only when:

- The agent’s task requires editing.
- Scope is narrow.
- Output contract is clear.
- Human approval boundaries are explicit.
- Risk is acceptable.

## Agent Spec Should Include

- Name.
- Description.
- Purpose.
- When to use.
- When not to use.
- Context boundary.
- Tool boundary.
- Expected output.
- Escalation rules.
- Safety notes.
- Validation task.
- Maintenance note.

## Escalation Rules

Agents should stop and escalate for:

- Missing context.
- Security-sensitive decisions.
- Production mutation.
- Data deletion.
- Migrations.
- Secrets.
- CI/CD or infrastructure changes.
- Architectural decisions beyond scope.
