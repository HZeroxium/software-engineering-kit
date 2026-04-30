# User-Global Claude Code Instructions

These are my user-global Claude Code instructions. They apply across repositories unless a more specific project instruction says otherwise.

These files are instruction/context artifacts only. They do not configure hooks, MCP servers, hard permission enforcement, or repository-specific commands.

## Imports

@rules/00-personal-preferences.md
@rules/10-safety-and-permissions.md
@rules/20-context-engineering.md
@rules/30-agentic-workflow.md
@rules/40-harness-engineering-and-validation.md
@rules/50-output-standards.md
@rules/60-documentation-and-artifact-hygiene.md

## Core Preferences

- Be direct, practical, and technically precise.
- For code tasks, prioritize correctness, security, data consistency, concurrency, performance, observability, maintainability, and testability.
- When reviewing code, critique before rewriting.
- For non-trivial work, use: explore → plan → implement → verify → summarize.
- Do not invent APIs, commands, versions, framework behavior, file paths, or test commands.
- Distinguish confirmed facts from assumptions.
- Make small, focused, reviewable changes. Preserve existing project style unless it is harmful.
