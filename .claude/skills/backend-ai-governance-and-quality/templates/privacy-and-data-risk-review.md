# Privacy and Data Risk Review

## Scope

`<feature/API/RAG workflow/model call/tool workflow>`

## Data Classification

| Data Type | Sensitivity                                                | Source     | Destination | Notes     |
| --------- | ---------------------------------------------------------- | ---------- | ----------- | --------- |
| `<data>`  | `<public/internal/sensitive/secret/PII/regulated/unknown>` | `<source>` | `<sink>`    | `<notes>` |

## Data Flow

```text
input -> validation -> processing -> storage -> retrieval/context -> model/tool -> logs/events/metrics -> response
```

## Privacy Risks

| Risk     | Location        | Severity     | Mitigation     |
| -------- | --------------- | ------------ | -------------- |
| `<risk>` | `<source/sink>` | `<severity>` | `<mitigation>` |

## Data Minimization

- **Can remove:** `<data>`
- **Can mask/tokenize:** `<data>`
- **Must not send to model:** `<data>`
- **Must not log:** `<data>`

## Retention / Deletion

| Data     | Retention Need | Deletion Requirement | Unknowns    |
| -------- | -------------- | -------------------- | ----------- |
| `<data>` | `<need>`       | `<requirement>`      | `<unknown>` |

## External Sharing

| Destination                    | Data Sent |   Approval Needed? | Risk     |
| ------------------------------ | --------- | -----------------: | -------- |
| `<model provider/tool/vendor>` | `<data>`  | `<yes/no/unknown>` | `<risk>` |

## Validation

- `<redaction test>`
- `<privacy review>`
- `<data flow review>`
- `<logging/metrics/traces review>`
- `<external provider review>`
