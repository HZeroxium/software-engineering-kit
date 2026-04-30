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
