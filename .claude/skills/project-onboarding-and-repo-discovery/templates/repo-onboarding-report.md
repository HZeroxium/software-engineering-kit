# Repository Onboarding Report

## Summary

- **Repository:** `<repo-name-or-path>`
- **Primary purpose:** `<confirmed / likely / unknown>`
- **Primary language(s):** `<languages>`
- **Main application type:** `<backend / frontend / CLI / library / DevOps / AI app / mixed / unknown>`
- **Frameworks confirmed:** `<frameworks or none confirmed>`
- **Internal libraries detected:** `<yes/no/unknown>`
- **Read-only status:** No files modified.

## Confidence Legend

- **Confirmed:** Directly supported by repository files, code, configs, or tests.
- **Likely:** Inferred from multiple consistent repository signals.
- **Assumption:** Plausible but not directly confirmed.
- **Unknown:** Requires deeper inspection or user input.

## Repository Root and Top-Level Structure

| Item           | Classification               | Evidence         | Notes     |
| -------------- | ---------------------------- | ---------------- | --------- |
| Repo root      | Confirmed                    | `<path / files>` | `<notes>` |
| Main modules   | `<Confirmed/Likely>`         | `<files/dirs>`   | `<notes>` |
| Docs           | `<Confirmed/Likely>`         | `<files>`        | `<notes>` |
| Config dirs    | `<Confirmed/Likely>`         | `<files/dirs>`   | `<notes>` |
| Generated code | `<Confirmed/Likely/Unknown>` | `<files/dirs>`   | `<notes>` |

## Project Purpose

### Confirmed facts

- `<fact>` — Evidence: `<file/path/symbol>`

### Likely interpretation

- `<interpretation>`

### Unknowns

- `<unknown>`

## Language and Technology Inventory

| Area             | Confirmed Technology                 | Evidence  | Notes     |
| ---------------- | ------------------------------------ | --------- | --------- |
| Runtime language | `<Java/Python/TypeScript/etc.>`      | `<files>` | `<notes>` |
| Build system     | `<Maven/Gradle/npm/Make/etc.>`       | `<files>` | `<notes>` |
| Test harness     | `<JUnit/pytest/Jest/etc.>`           | `<files>` | `<notes>` |
| API/RPC          | `<REST/gRPC/GraphQL/custom/unknown>` | `<files>` | `<notes>` |
| Persistence      | `<SQL/NoSQL/files/unknown>`          | `<files>` | `<notes>` |
| Observability    | `<logging/metrics/tracing>`          | `<files>` | `<notes>` |
| Deployment       | `<Docker/K8s/systemd/unknown>`       | `<files>` | `<notes>` |

## Module and Package Layout

| Module/Directory | Role     | Evidence          | Notes     |
| ---------------- | -------- | ----------------- | --------- |
| `<path>`         | `<role>` | `<files/classes>` | `<notes>` |

## Runtime Entrypoints

| Entrypoint            | Type                            | Evidence | How it starts      | Notes     |
| --------------------- | ------------------------------- | -------- | ------------------ | --------- |
| `<class/file/script>` | `<server/CLI/worker/test/etc.>` | `<path>` | `<command/config>` | `<notes>` |

## Build, Test, and Validation Commands

See `build-and-test-command-discovery.md` format for detailed evidence.

### Confirmed commands

- `<command>` — Evidence: `<file/path>`

### Candidate commands

- `<command>` — Evidence: `<file/path>` — Risk: `<risk>`

### Unknown commands

- `<missing command type>`

## Internal Library Inventory

See `internal-library-inventory.md` format for details.

### High-signal internal abstractions

- `<library/namespace>` — Used for `<purpose>` — Evidence: `<files>`

## Configuration and Environment

| Config Area | Files     | Purpose     | Risk     |
| ----------- | --------- | ----------- | -------- |
| `<area>`    | `<files>` | `<purpose>` | `<risk>` |

## CI/CD and Deployment Signals

| Area             | Evidence  | Interpretation     | Risk     |
| ---------------- | --------- | ------------------ | -------- |
| CI               | `<files>` | `<interpretation>` | `<risk>` |
| Containerization | `<files>` | `<interpretation>` | `<risk>` |
| Deployment       | `<files>` | `<interpretation>` | `<risk>` |

## Generated Code and Code Ownership

| Path     | Generator Signal | Should edit manually? | Notes     |
| -------- | ---------------- | --------------------- | --------- |
| `<path>` | `<evidence>`     | `<no/unknown>`        | `<notes>` |

## Risk Areas

| Risk Area       | Evidence  | Why It Matters | Safe Handling |
| --------------- | --------- | -------------- | ------------- |
| Auth/security   | `<files>` | `<reason>`     | `<guidance>`  |
| Secrets/config  | `<files>` | `<reason>`     | `<guidance>`  |
| Migrations/data | `<files>` | `<reason>`     | `<guidance>`  |
| CI/CD/infra     | `<files>` | `<reason>`     | `<guidance>`  |
| Generated code  | `<files>` | `<reason>`     | `<guidance>`  |

## Recommended Next Files to Inspect

1. `<path>` — `<why>`
2. `<path>` — `<why>`
3. `<path>` — `<why>`

## Open Questions

1. `<question>`
2. `<question>`
3. `<question>`

## AI-Ready Context Block

Paste the compact context block here or link to the generated context block section.

## Safe Next Action

`<recommended next action, read-only unless user explicitly requests edits>`
