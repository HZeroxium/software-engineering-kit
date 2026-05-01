# Internal Library Inventory

## Summary

- **Internal libraries detected:** `<yes/no/unknown>`
- **Primary namespaces/prefixes:** `<list>`
- **Confidence:** `<high/medium/low>`
- **Main risk:** Do not infer behavior without code usage, tests, or documentation evidence.

## Library Inventory

| Library / Namespace | Observed Purpose | Evidence               | Confidence          | Unknowns     |
| ------------------- | ---------------- | ---------------------- | ------------------- | ------------ |
| `<library>`         | `<purpose>`      | `<files/usages/tests>` | `<high/medium/low>` | `<unknowns>` |

## Usage Patterns

### Bootstrap / Startup

| Pattern                               | Evidence  | Notes     |
| ------------------------------------- | --------- | --------- |
| `<class/function/annotation/factory>` | `<files>` | `<notes>` |

### Dependency Injection / Object Construction

| Pattern                                 | Evidence  | Notes     |
| --------------------------------------- | --------- | --------- |
| `<constructor/factory/module/provider>` | `<files>` | `<notes>` |

### RPC / API / Messaging Abstractions

| Pattern                              | Evidence  | Notes     |
| ------------------------------------ | --------- | --------- |
| `<client/server/wrapper/annotation>` | `<files>` | `<notes>` |

### Configuration Loading

| Pattern                                       | Evidence  | Notes     |
| --------------------------------------------- | --------- | --------- |
| `<config loader/property binding/env reader>` | `<files>` | `<notes>` |

### Logging / Metrics / Tracing

| Pattern                   | Evidence  | Notes     |
| ------------------------- | --------- | --------- |
| `<logger/metrics/tracer>` | `<files>` | `<notes>` |

### Testing Utilities

| Pattern                            | Evidence  | Notes     |
| ---------------------------------- | --------- | --------- |
| `<test helper/base class/fixture>` | `<files>` | `<notes>` |

## Import and Usage Evidence

| Import / Symbol   | Production Usage | Test Usage | Interpretation     |
| ----------------- | ---------------- | ---------- | ------------------ |
| `<import/symbol>` | `<files>`        | `<files>`  | `<interpretation>` |

## Safe Usage Rules

- Prefer existing usage examples over documentation claims.
- Prefer tests and integration examples when available.
- Do not introduce new internal-library APIs unless a matching usage pattern already exists or the user confirms the API.
- If behavior is unclear, ask for internal docs or source access.
- Mark gaps explicitly.

## Open Questions

1. `<question about internal lib behavior>`
2. `<question about ownership/versioning>`
3. `<question about safe extension points>`
