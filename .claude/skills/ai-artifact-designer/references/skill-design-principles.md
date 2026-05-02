---
purpose: Criteria for creating vs avoiding Skills; SKILL.md structure guidance; reference file tier convention for progressive context loading
load-when: Task involves designing, evaluating, or structuring a Skill or its supporting files
tier: domain
see-also:
  - artifact-taxonomy.md
  - naming-conventions.md
---

# Skill Design Principles

## Good Skill Candidates

Create a Skill when:

- The workflow repeats often.
- The trigger is easy to describe.
- The procedure has a stable shape.
- The output has a reusable format.
- Supporting templates/checklists/examples help.
- You want progressive context loading.

## Poor Skill Candidates

Avoid a Skill when:

- The task is one-off.
- The workflow is vague.
- It requires live external data.
- It needs hard enforcement.
- It is better as a short prompt.
- It duplicates existing global guidance.
- It combines too many unrelated workflows.

## SKILL.md Guidance

Keep `SKILL.md` concise:

- Purpose.
- When to use.
- When not to use.
- Required inputs.
- Workflow.
- Output format.
- Safety boundaries.
- Validation.
- Supporting files.

Move deep detail into:

- `references/`
- `templates/`
- `checklists/`
- `examples/`

## Description Quality

A good description should include:

- Main trigger phrases.
- Task type.
- Scope.
- Important exclusions.
- Tool-specific constraints.

Avoid descriptions that are:

- Too generic.
- Too long.
- Missing trigger verbs.
- Overlapping with many other Skills.

## Validation

Test a Skill with:

- Direct slash invocation.
- Automatic activation prompt.
- Boundary prompt that should not activate it.
- Small realistic task.
- Output quality review.

## Reference File Tier Convention

When designing supporting `references/` files for a Skill, classify each reference
by tier to enable progressive context loading and prevent circular dependencies.

### Tiers

#### foundational

- No dependencies on other references in this skill.
- Provides vocabulary, taxonomy, or core principles used by domain and scenario references.
- Load first when general classification is needed.
- Example: `artifact-taxonomy.md`

#### domain

- Extends a foundational reference for a specific artifact type or workflow area.
- May reference foundational references via `see-also`.
- Load only when the task targets that domain.
- Example: `skill-design-principles.md`, `agent-design-principles.md`

#### scenario

- Activated only when a specific condition or decision point is detected.
- May reference foundational and domain references via `see-also`.
- Do not reference other scenario references — prevents circular loading.
- Example: `overengineering-risks.md`

### `see-also` Semantic

`see-also` is a **forward navigation pointer**, not a dependency declaration. It means:
"after reading this file, also consider loading these files based on the current task."
A foundational file has no upstream dependencies but may point forward to domain files
as navigation hints for the agent.

### Navigation Rules

```text
foundational → no upstream dependencies; see-also may point forward to domain or scenario files
domain       → no upstream dependencies on scenario; see-also may point to foundational or other domain
scenario     → no upstream dependencies on other scenario; see-also may point to foundational or domain
```

Avoid bidirectional `see-also` between peer files at the same tier. If A points to B,
B should not also point back to A. Use `see-also: []` for terminal leaf files.

### YAML Frontmatter for Reference Files

Every reference file should include a YAML frontmatter block with 4 fields:

```yaml
---
purpose: One-line description of what this reference covers
load-when: The condition that triggers loading this file
tier: foundational | domain | scenario
see-also:
  - related-reference.md   # forward navigation hints only; [] for terminal leaves
---
```

Keep `see-also` to the most directly useful forward pointers only.
