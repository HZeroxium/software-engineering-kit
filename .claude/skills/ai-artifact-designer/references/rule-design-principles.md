---
purpose: Criteria for Good vs Poor rules; numbering convention (00–60); conflict avoidance between rules and skills
load-when: Task involves designing, evaluating, or specifying a rule in rules/*.md
tier: domain
see-also:
  - artifact-taxonomy.md
  - naming-conventions.md
---

# Rule Design Principles

## Good Rule Candidates

Use rules for stable, global behavior such as:

- Communication preferences.
- Safety boundaries.
- Context engineering.
- Workflow discipline.
- Validation expectations.
- Output standards.
- Documentation hygiene.

## Poor Rule Candidates

Avoid rules for:

- One-off tasks.
- Long procedures.
- Repo-specific commands.
- Tool-specific deep workflows.
- Large examples.
- Content better suited to a Skill.

## Rule Design

Rules should be:

- Stable.
- Short.
- Clear.
- Non-duplicative.
- Easy to audit.
- Independent where possible.
- Not overloaded with examples.

## Numbering Convention

Use numbered prefixes for ordering:

- `00-` personal preferences.
- `10-` safety and permissions.
- `20-` context engineering.
- `30-` workflow.
- `40-` validation.
- `50-` output standards.
- `60-` documentation hygiene.

Adjust only when there is a clear reason.

## Conflict Avoidance

Avoid repeating detailed task workflow in both:

- `rules/*.md`
- Skills
- Agents
- Repo docs

Keep global rules stable. Put task-specific steps in Skills.
