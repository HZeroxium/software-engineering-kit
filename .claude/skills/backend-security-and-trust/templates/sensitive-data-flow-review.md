# Sensitive Data Flow Review

## Data

`<sensitive data type>`

## Classification

- [ ] Public
- [ ] Internal
- [ ] Sensitive
- [ ] Secret
- [ ] Personal data / PII
- [ ] Regulated data
- [ ] Unknown

## Data Flow

```text
source -> validation -> processing -> storage -> logs/events/metrics -> external systems -> response
```

## Sources and Sinks

| Location          | Data Present? | Protection     | Risk     |
| ----------------- | ------------: | -------------- | -------- |
| API request       |    `<yes/no>` | `<protection>` | `<risk>` |
| Database          |    `<yes/no>` | `<protection>` | `<risk>` |
| Cache             |    `<yes/no>` | `<protection>` | `<risk>` |
| Logs              |    `<yes/no>` | `<protection>` | `<risk>` |
| Metrics/traces    |    `<yes/no>` | `<protection>` | `<risk>` |
| Events/messages   |    `<yes/no>` | `<protection>` | `<risk>` |
| External provider |    `<yes/no>` | `<protection>` | `<risk>` |
| API response      |    `<yes/no>` | `<protection>` | `<risk>` |

## Minimization

- `<data that can be removed/masked/tokenized>`

## Validation

- `<log redaction review>`
- `<response field test>`
- `<event payload review>`
- `<external provider data review>`
