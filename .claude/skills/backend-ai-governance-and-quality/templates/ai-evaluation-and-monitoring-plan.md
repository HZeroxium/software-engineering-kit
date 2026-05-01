# AI Evaluation and Monitoring Plan

## AI Feature

`<feature>`

## Quality Bar

| Metric / Criterion          | Target     | Notes     |
| --------------------------- | ---------- | --------- |
| Task success                | `<target>` | `<notes>` |
| Groundedness / faithfulness | `<target>` | `<notes>` |
| Retrieval quality           | `<target>` | `<notes>` |
| Safety policy pass rate     | `<target>` | `<notes>` |
| Latency                     | `<target>` | `<notes>` |
| Cost                        | `<target>` | `<notes>` |

## Evaluation Dataset

| Dataset     | Purpose     | Source     | Risk     |
| ----------- | ----------- | ---------- | -------- |
| `<dataset>` | `<purpose>` | `<source>` | `<risk>` |

## Test Cases

| Case     | Expected Behavior | Failure Signal |
| -------- | ----------------- | -------------- |
| `<case>` | `<expected>`      | `<failure>`    |

## Evaluation Methods

- `<exact match / rubric / LLM-as-judge / human review / retrieval metrics / task-specific metric>`
- `<method>`

## Monitoring

| Signal          | Purpose     | Alert / Review Trigger |
| --------------- | ----------- | ---------------------- |
| Latency         | `<purpose>` | `<trigger>`            |
| Cost            | `<purpose>` | `<trigger>`            |
| Quality         | `<purpose>` | `<trigger>`            |
| Safety          | `<purpose>` | `<trigger>`            |
| Provider errors | `<purpose>` | `<trigger>`            |
| Retrieval drift | `<purpose>` | `<trigger>`            |

## Release Gate

- [ ] Offline evaluation passed.
- [ ] Safety review completed.
- [ ] Privacy review completed.
- [ ] Monitoring exists.
- [ ] Rollback/disable path exists.
- [ ] Human approval boundaries defined.
