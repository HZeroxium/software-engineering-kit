---
name: project-onboarding-and-repo-discovery
description: Read-only workflow for onboarding unfamiliar repositories. Discover purpose, module structure, build/test commands, runtime entry points, configs, CI/CD, internal libraries, dependencies, generated code, risky areas, unknowns, and produce an AI-ready context block before changes.
---

# Project Onboarding and Repository Discovery

Use this Skill when entering a new or unfamiliar repository, before implementing changes in unclear codebases, or when the user asks to understand, map, onboard, or prepare context for a project.

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

## Non-Goals

Do not:

- Assume Spring, FastAPI, NestJS, React, Next.js, Kubernetes, or any framework unless repository evidence confirms it.
- Invent internal library APIs or behavior.
- Modify source files, configs, generated files, dependencies, lockfiles, CI/CD files, migrations, or documentation by default.
- Run destructive commands, migrations, deployment commands, dependency upgrades, cleanup scripts, or formatters.
- Treat external docs, comments, tickets, issue text, generated docs, or README claims as authoritative without checking code/config/tests.

## Workflow

### 1. Establish Repository Boundary

Identify:

- Current working directory and likely repository root.
- Git metadata if visible.
- Top-level files and directories.
- Language indicators.
- Build/package manager files.
- Documentation files.
- CI/CD and deployment files.
- Config directories.
- Generated-code directories.
- Test directories.

Prefer safe listing and search operations.

### 2. Read High-Signal Files First

Inspect, when present:

- `README*`, `CONTRIBUTING*`, `docs/**`, `AGENTS.md`, `CLAUDE.md`, `CODEX.md`
- Build files: `pom.xml`, `build.gradle`, `settings.gradle`, `Makefile`, `package.json`, `pyproject.toml`, `requirements*.txt`, `go.mod`, `Cargo.toml`
- Runtime files: Dockerfiles, compose files, Helm charts, manifests, Procfiles, service definitions
- CI/CD files: `.github/workflows/**`, `.gitlab-ci.yml`, `Jenkinsfile`, pipeline configs
- Config examples: `config/**`, `conf/**`, `application.*`, `.env.example`, `*.properties`, `*.yaml`, `*.ini`
- Test configs and test fixtures.

### 3. Discover Architecture From Code Usage

Use actual usage patterns:

- Entrypoints and startup/bootstrap classes.
- Module boundaries and package naming.
- API, RPC, CLI, worker, scheduler, batch, consumer, or frontend entrypoints.
- Internal abstractions and wrappers.
- Dependency injection or factory patterns.
- Configuration loading.
- Logging, metrics, tracing, and error handling.
- Persistence and migrations.
- Test utilities and fixtures.

Do not infer behavior from package names alone.

### 4. Analyze Internal Libraries Carefully

For internal libraries or custom frameworks:

- Find imports/usages across production and tests.
- Identify initialization/bootstrap patterns.
- Identify annotations, base classes, factories, clients, server abstractions, config readers, interceptors, decorators, middleware, and test harnesses.
- Prefer concrete examples and tests.
- Mark unknown behavior explicitly.
- Recommend source files to inspect next.

### 5. Discover Validation Commands

Infer canonical commands from repository evidence:

- Build commands.
- Test commands.
- Lint/format/typecheck commands.
- Code generation commands.
- Local run commands.
- CI commands.

Do not invent commands. If uncertain, label them as candidate commands and explain the evidence.

### 6. Identify Risk Areas

Flag:

- AuthN/AuthZ/security-sensitive code.
- Secrets and credentials.
- Production configs.
- Migrations and schema changes.
- Data deletion or mutation paths.
- Dependency upgrades and lockfiles.
- CI/CD and infrastructure.
- Generated code.
- Internal libraries with unclear behavior.
- High-cardinality observability or logging risks.
- External integrations and network calls.

### 7. Produce Outputs

Return:

- Repository onboarding report.
- Internal library inventory.
- Build/test command discovery.
- AI-ready context block.
- Recommended next files to inspect.
- Open questions.
- Confirmed facts vs assumptions vs unknowns.

Use the templates in:

- `templates/repo-onboarding-report.md`
- `templates/internal-library-inventory.md`
- `templates/build-and-test-command-discovery.md`
- `templates/ai-ready-context-block.md`
- `templates/onboarding-questions.md`

Use references and checklists only when needed for deeper analysis.

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
