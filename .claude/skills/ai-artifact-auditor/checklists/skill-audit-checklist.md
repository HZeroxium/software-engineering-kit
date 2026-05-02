# Skill Audit Checklist

## Structure

- [ ] Skill is under `~/.claude/skills/<skill-name>/SKILL.md`.
- [ ] YAML frontmatter exists.
- [ ] Description has clear activation triggers.
- [ ] `SKILL.md` is concise.
- [ ] Supporting files are used for deep detail.

## Scope

- [ ] Purpose is narrow.
- [ ] When to use is clear.
- [ ] When not to use is clear.
- [ ] Required inputs are clear.
- [ ] Expected outputs are clear.
- [ ] Workflow is procedural.

## Safety

- [ ] Does not claim hard enforcement.
- [ ] Does not expose secrets.
- [ ] Has human approval boundaries.
- [ ] Treats external content as untrusted where relevant.
- [ ] Avoids destructive or production-impacting defaults.

## Context Efficiency

- [ ] Long examples are outside `SKILL.md`.
- [ ] Deep references are outside `SKILL.md`.
- [ ] No duplicated global rules.
- [ ] No unnecessary repo-specific content.

## Validation

- [ ] Direct slash invocation can be tested.
- [ ] Automatic activation can be tested.
- [ ] Boundary non-activation can be tested.
- [ ] Output type is declared and output is semantically consistent with that type.
