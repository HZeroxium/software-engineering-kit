# Naming Conventions

## Skills

Use:

- `<domain>-<workflow>`
- `<workflow>`

Examples:

- `code-review`
- `testing-and-validation`
- `debugging-workflow`
- `ai-artifact-designer`
- `requirements-analysis-and-estimation`

Avoid:

- `best-skill`
- `general-helper`
- `developer-agent`
- `do-everything`
- Names that overlap with built-ins unless intentional.

## Agents

Use:

- `<domain>-reviewer`
- `<risk>-reviewer`
- `<workflow>-assistant`
- `<domain>-auditor`

Examples:

- `security-reviewer`
- `java-code-reviewer`
- `docs-maintenance-assistant`
- `ai-artifact-auditor`

Avoid:

- `super-agent`
- `senior-engineer`
- `assistant`
- `general-reviewer` when scope is unclear.

## Rules

Use:

- Numbered prefix.
- Stable topic.
- Lowercase kebab-case.

Examples:

- `00-personal-preferences.md`
- `10-safety-and-permissions.md`
- `20-context-engineering.md`

Avoid:

- Unnumbered random rules.
- Long changing task-specific filenames.
- Duplicates with different names.

## Supporting Files

Use folders by function:

- `templates/`
- `references/`
- `examples/`
- `checklists/`

Prefer descriptive filenames:

- `skill-design-principles.md`
- `artifact-portfolio-recommendation.md`
- `skill-audit-checklist.md`
