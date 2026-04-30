# CLAUDE.md and Rules Audit Checklist

## CLAUDE.md

- [ ] Short and stable.
- [ ] Imports rules where appropriate.
- [ ] Contains only durable global preferences.
- [ ] Does not contain long task procedures.
- [ ] Does not duplicate Skill instructions.
- [ ] Does not include repo-specific commands.
- [ ] Does not claim enforcement.

## Rules

- [ ] Rule filenames use numbered prefixes.
- [ ] Each rule has a stable topic.
- [ ] Rules are concise.
- [ ] Task-specific procedures are moved to Skills.
- [ ] Safety boundaries are clear.
- [ ] Validation expectations are clear.
- [ ] No duplicate/conflicting rules exist.

## Context Efficiency

- [ ] Always-loaded content is minimal.
- [ ] Deep guidance lives in Skills or supporting files.
- [ ] Examples are not loaded globally unless necessary.
- [ ] Rules are not overloaded.

## Safety

- [ ] Secrets are not included.
- [ ] External content is treated as untrusted.
- [ ] Human approval boundaries exist.
- [ ] High-risk work is called out.
- [ ] Hooks/MCP are not implied unless configured elsewhere.

## Maintenance

- [ ] Update triggers are documented.
- [ ] Stale guidance is removed.
- [ ] Conflicts with repo-level artifacts are noted.
- [ ] Repeated AI failures map to specific rule updates.
