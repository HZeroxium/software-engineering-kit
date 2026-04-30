# Conflict Resolution

## Priority Model

When artifacts conflict, prefer:

1. User’s current explicit instruction.
2. Safety-critical instruction.
3. More specific scope.
4. More current artifact.
5. Canonical global instruction for stable preferences.
6. Skill for task-specific workflow.
7. Agent for delegated bounded work.
8. Supporting reference for deep detail.

## Common Conflicts

### Global Rule vs Skill

Resolution:

- Keep stable behavior in global rule.
- Move workflow procedure into Skill.

### Skill vs Skill

Resolution:

- Split by workflow trigger.
- Merge if triggers and outputs are effectively identical.
- Narrow descriptions.

### Agent vs Skill

Resolution:

- Use Skill for procedure.
- Use Agent for separate context or bounded delegation.
- Do not duplicate the full procedure in both.

### User-Global vs Repo-Specific

Resolution:

- Keep personal preferences global.
- Keep repo commands and conventions repo-specific.
- Repo-specific guidance should override generic assumptions.

## Fix Pattern

1. Identify canonical source.
2. Remove or reduce duplicate content.
3. Add cross-reference only when needed.
4. Narrow activation descriptions.
5. Smoke-test behavior.
