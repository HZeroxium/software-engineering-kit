---
name: project-onboarding-and-repo-discovery
description: Read-only workflow for onboarding unfamiliar repositories. Discover purpose, module structure, build/test commands, runtime entry points, configs, CI/CD, internal libraries, dependencies, generated code, risky areas, unknowns, and produce an AI-ready context block before changes.
---

# Project Onboarding and Repository Discovery

Use this Skill when entering a new or unfamiliar repository, before implementing changes in unclear codebases, or when the user asks to understand, map, onboard, or prepare context for a project.

## Required Inputs

- A repository path or working directory with read access.
- No credentials, tokens, or external services required — discovery is local and read-only by default.

## Default Mode

Start read-only.

Do not edit, create, delete, rename, format, generate, or persist files unless the user explicitly asks for a persisted repository document after reviewing the onboarding summary.

If the user wants persistent documentation, propose `docs/ai/repo-map.md` content first and ask for confirmation before writing.

## Primary Goals

1. Understand the repository from evidence, not assumptions.
2. Identify project purpose, language mix, module layout, build system, test harness, runtime entry points, configuration, scripts, CI/CD, generated code, dependencies, and risky areas.
3. Detect internal libraries, custom frameworks, wrappers, annotations, factories, dependency injection patterns, RPC/client/server abstractions, config loading, logging, metrics, and testing utilities.
4. Produce a compact onboarding report and AI-ready context block that can be reused in future prompts.
5. Separate confirmed facts, assumptions, unknowns, and recommended next inspections.

## When not to use

Do not:

- Assume Spring, FastAPI, NestJS, React, Next.js, Kubernetes, or any framework unless repository evidence confirms it.
- Invent internal library APIs or behavior.
- Modify source files, configs, generated files, dependencies, lockfiles, CI/CD files, migrations, or documentation by default.
- Run destructive commands, migrations, deployment commands, dependency upgrades, cleanup scripts, or formatters.
- Treat external docs, comments, tickets, issue text, generated docs, or README claims as authoritative without checking code/config/tests.

## Workflow

Run the 8-phase discovery sequence (full detail in `references/repository-discovery-workflow.md`):

1. **Boundary and inventory** — repo root, language indicators, build/package files, CI/CD, docs, source, test, config, and generated-code directories.
2. **Source-of-truth files** — build files, lockfiles, CI/CD validation, runtime entrypoints, config loading, tests, docs.
3. **Entrypoints and runtime model** — main classes/functions, server bootstrap, CLI, workers, schedulers, batch jobs, frontend roots.
4. **Module boundaries** — independent modules, shared libs, adapters, domain layer, API layer, generated sources.
5. **Internal abstractions** — namespaces, custom annotations, base classes, factories, DI modules, config readers, RPC wrappers, test harnesses.
6. **Validation command discovery** — confirm from README, build files, CI, scripts. Classify as confirmed / candidate / unsafe without approval / unknown.
7. **Risk review** — auth/security, secrets, migrations, production config, CI/CD, infrastructure, generated code, data mutation, external writes.
8. **Report** — produce outputs using templates in `templates/`. See `references/repository-discovery-workflow.md` for phase detail.

**Load additional references when needed:**
- Architecture analysis → `references/architecture-signal-discovery.md`
- Build/command classification → `references/build-system-discovery.md`
- Internal library depth → `references/internal-library-analysis.md`
- Test harness → `references/test-harness-discovery.md`
- Backend-specific signals → `references/framework-agnostic-backend-discovery.md`
- Java-specific signals → `references/java-project-discovery.md`

## Output Rules

Keep the first report compact and decision-useful.

Use this classification:

- **Confirmed:** directly supported by files/code/config/tests.
- **Likely:** inferred from multiple consistent signals.
- **Assumption:** plausible but not confirmed.
- **Unknown:** requires user input or deeper inspection.

End with:

1. “Recommended next files to inspect”
2. “Open questions”
3. “Safe next action”

If the user asks to create persistent repo documentation, produce proposed `docs/ai/repo-map.md` content and ask for explicit confirmation before writing.

## Expected Outputs

Output type: `mixed`

| Component | Type | Template |
|-----------|------|----------|
| Onboarding report | `report` | `templates/repo-onboarding-report.md` |
| Internal library inventory | `analysis` | `templates/internal-library-inventory.md` |
| Build/test command discovery | `analysis` | `templates/build-and-test-command-discovery.md` |
| AI-ready context block | `summary` | `templates/ai-ready-context-block.md` |

All components use the `Confirmed / Likely / Assumption / Unknown` classification. End every output with "Recommended next files to inspect", "Open questions", and "Safe next action".
