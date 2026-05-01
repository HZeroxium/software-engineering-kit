# Build and Test Command Discovery

## Summary

- **Build system:** `<confirmed/likely/unknown>`
- **Package manager:** `<confirmed/likely/unknown>`
- **Test framework:** `<confirmed/likely/unknown>`
- **Canonical validation command:** `<command or unknown>`
- **Confidence:** `<high/medium/low>`

## Evidence Sources

| Source   | Relevant Signal               | Interpretation     |
| -------- | ----------------------------- | ------------------ |
| `<file>` | `<script/plugin/task/config>` | `<interpretation>` |

## Confirmed Commands

| Task              | Command     | Evidence             | Notes     |
| ----------------- | ----------- | -------------------- | --------- |
| Build             | `<command>` | `<file/line/signal>` | `<notes>` |
| Unit tests        | `<command>` | `<file/line/signal>` | `<notes>` |
| Integration tests | `<command>` | `<file/line/signal>` | `<notes>` |
| Lint              | `<command>` | `<file/line/signal>` | `<notes>` |
| Format check      | `<command>` | `<file/line/signal>` | `<notes>` |
| Typecheck         | `<command>` | `<file/line/signal>` | `<notes>` |
| Local run         | `<command>` | `<file/line/signal>` | `<notes>` |
| Code generation   | `<command>` | `<file/line/signal>` | `<notes>` |
| CI validation     | `<command>` | `<file/line/signal>` | `<notes>` |

## Candidate Commands

Use this section when command evidence is incomplete.

| Task     | Candidate Command | Evidence | Risk / Caveat |
| -------- | ----------------- | -------- | ------------- |
| `<task>` | `<command>`       | `<file>` | `<risk>`      |

## Commands Not Found

- `<build/test/lint/typecheck/run/codegen/etc.>`

## Safety Notes

- Do not run commands that mutate dependencies, generate code, migrate databases, deploy, publish, delete files, or modify infrastructure without user approval.
- Prefer dry-run, help, list, or read-only inspection commands before execution.
- If commands depend on internal tooling, ask the user before invoking them.
- If the repo has multiple modules, validate the smallest relevant module first when possible.

## Recommended Validation Sequence

1. `<safe command or inspection step>`
2. `<safe command or inspection step>`
3. `<safe command or inspection step>`
