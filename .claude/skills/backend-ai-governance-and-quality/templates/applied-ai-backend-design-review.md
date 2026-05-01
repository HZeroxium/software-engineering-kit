# Applied AI Backend Design Review

## Summary

- **AI capability:** `<capability>`
- **AI task type:** `<classification/generation/search/extraction/tool orchestration/etc.>`
- **Model/provider:** `<model/provider/unknown>`
- **Risk level:** `<low/medium/high/critical>`
- **Recommendation:** `<approve / revise / block / needs evaluation>`

## AI Appropriateness

| Question                            | Answer             | Notes     |
| ----------------------------------- | ------------------ | --------- |
| Is AI necessary?                    | `<yes/no/unclear>` | `<notes>` |
| Is deterministic logic safer?       | `<yes/no>`         | `<notes>` |
| What is acceptable error tolerance? | `<tolerance>`      | `<notes>` |
| What is human impact if wrong?      | `<impact>`         | `<notes>` |

## Backend Architecture

```text
request -> validation -> context/retrieval -> model/tool call -> output validation -> persistence/side effects -> response
```

## Prompt / Context / Retrieval

| Area          | Design     | Risk     |
| ------------- | ---------- | -------- |
| Prompt        | `<design>` | `<risk>` |
| Context       | `<design>` | `<risk>` |
| Retrieval     | `<design>` | `<risk>` |
| Output schema | `<design>` | `<risk>` |
| Guardrails    | `<design>` | `<risk>` |

## Tool / Function Calling

| Tool     | Side Effect                           | Approval Needed? | Validation     |
| -------- | ------------------------------------- | ---------------: | -------------- |
| `<tool>` | `<read/write/external/data mutation>` |       `<yes/no>` | `<validation>` |

## AI Risks

- Prompt injection: `<risk>`
- Sensitive data leakage: `<risk>`
- Hallucination: `<risk>`
- Unsafe tool side effects: `<risk>`
- Cost/latency: `<risk>`
- Vendor/provider failure: `<risk>`

## Evaluation Plan

- `<offline eval>`
- `<golden dataset>`
- `<regression suite>`
- `<human review>`
- `<production monitoring>`

## Recommendation

`<recommended design changes before implementation/production>`
