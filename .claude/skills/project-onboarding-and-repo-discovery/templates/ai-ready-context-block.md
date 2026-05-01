# AI-Ready Context Block

Use this block in future prompts or repository-level AI artifacts.

## Context Block

```text
Repository: <repo-name-or-path>

Purpose:
- <confirmed purpose or likely interpretation>

Primary languages:
- <language>: <evidence>
- <language>: <evidence>

Application type:
- <backend/frontend/library/CLI/DevOps/AI app/mixed/unknown>

Architecture shape:
- <modules/layers/services/components>
- <entrypoints>
- <runtime model>

Build system:
- <confirmed build system>
- Evidence: <files>

Validation commands:
- Build: <command or unknown>
- Test: <command or unknown>
- Lint/typecheck: <command or unknown>
- Local run: <command or unknown>

Key directories:
- <path>: <purpose>
- <path>: <purpose>
- <path>: <purpose>

Internal libraries/custom framework signals:
- <library/namespace>: <observed purpose>, evidence: <files>
- <unknowns>

Configuration:
- <config paths and purpose>
- <environment assumptions>

CI/CD and deployment:
- <pipeline/deployment files>
- <container/orchestration signals>

Generated code:
- <paths>
- Manual edit policy: <avoid/unknown>

Risk areas:
- <auth/security/secrets/migrations/prod config/CI/CD/infra/generated code/dependencies>
- Required approval before touching: <areas>

Known unknowns:
- <unknown>
- <unknown>

Repository-specific rules inferred from evidence:
- <rule>
- <rule>

Safe next-step guidance for AI:
- Start read-only.
- Inspect relevant files before editing.
- Do not assume frameworks or internal APIs.
- Prefer existing conventions and tests.
- Ask before modifying high-risk areas.
- Validate with confirmed commands before claiming completion.
```
