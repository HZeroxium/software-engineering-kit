---
purpose: Classification of 6 AI artifact types (instruction artifact, skill, agent, hook, MCP, human approval boundary) with use cases, trade-offs, and risks
load-when: Classifying an extension type or deciding which artifact type fits the target workflow
tier: foundational
see-also:
  - skill-design-principles.md
  - agent-design-principles.md
  - rule-design-principles.md
---

# Artifact Taxonomy

## Instruction Artifact

Examples:

- `CLAUDE.md`
- `rules/*.md`
- AGENTS.md
- Copilot instructions
- Cursor rules
- Prompt files
- Workflow docs

Use when:

- Guidance is stable.
- Behavior should influence many tasks.
- No execution or external data access is needed.

Risk:

- Stale guidance.
- Conflicts.
- Too much always-loaded context.

## Skill

Use when:

- Workflow is repeated.
- Activation criteria are clear.
- Procedure has steps.
- Templates, examples, or references help.
- Context should load only when needed.

Risk:

- Over-broad Skill.
- Weak description.
- Duplicate procedure.
- Excessive supporting files.

## Agent / Subagent

Use when:

- Work benefits from separate context.
- Task is specialized.
- Exploration may flood main conversation.
- Tool access should be bounded.
- Independent review or analysis is useful.

Risk:

- Unclear ownership.
- Over-delegation.
- Unsafe tool access.
- Conflicting recommendations.
- Higher coordination cost.

## Hook

Use when:

- Lifecycle automation is needed.
- Pre-command or post-edit checks are useful.
- Enforcement/warning must happen at tool boundary.

Do not create in this phase.

Risk:

- Hidden side effects.
- Workflow friction.
- Fragile environment assumptions.

## MCP

Use when:

- Live external data or tools are needed.
- Controlled external access creates clear value.
- Tool/resource permissions can be managed.

Do not create in this phase.

Risk:

- Data exposure.
- Authorization gaps.
- Prompt/tool injection.
- Operational overhead.

## Human Approval Boundary

Use when:

- High-risk actions require explicit user decision.
- The assistant should stop before edits or commands.

Examples:

- Migrations.
- Auth/security changes.
- CI/CD.
- Infrastructure.
- Production configs.
- Secret handling.
- Destructive commands.
