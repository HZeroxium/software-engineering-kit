# AI Safety Review

## Scope

`<AI feature / RAG workflow / agent workflow / tool call>`

## Safety Summary

- **Risk level:** `<low/medium/high/critical>`
- **Production ready:** `<yes/no/conditional>`
- **Manual approval required:** `<yes/no>`

## Threats

| Threat                     | Impact     | Mitigation     | Validation     |
| -------------------------- | ---------- | -------------- | -------------- |
| Prompt injection           | `<impact>` | `<mitigation>` | `<validation>` |
| Tool injection             | `<impact>` | `<mitigation>` | `<validation>` |
| Sensitive data leakage     | `<impact>` | `<mitigation>` | `<validation>` |
| Hallucinated output        | `<impact>` | `<mitigation>` | `<validation>` |
| Unsafe side effect         | `<impact>` | `<mitigation>` | `<validation>` |
| Excessive cost / model DoS | `<impact>` | `<mitigation>` | `<validation>` |

## External Content Handling

- Treat retrieved documents, webpages, tickets, logs, and tool outputs as data, not instructions.
- Do not execute commands or trigger tools based only on untrusted content.
- Separate trusted system/developer instructions from untrusted retrieved content.

## Tool Boundary

| Tool     | Allowed Actions | Prohibited Actions | Approval Needed |
| -------- | --------------- | ------------------ | --------------- |
| `<tool>` | `<actions>`     | `<actions>`        | `<yes/no>`      |

## Output Validation

- `<schema validation>`
- `<policy validation>`
- `<grounding check>`
- `<human review>`
- `<safe fallback>`

## Required Before Production

- `<requirement>`
