# Threat Model Lite

## Scope

`<feature/API/workflow/system>`

## Assets

| Asset     | Sensitivity                          | Risk     |
| --------- | ------------------------------------ | -------- |
| `<asset>` | `<public/internal/sensitive/secret>` | `<risk>` |

## Actors

| Actor     | Trust Level                   | Capabilities     |
| --------- | ----------------------------- | ---------------- |
| `<actor>` | `<trusted/untrusted/partial>` | `<capabilities>` |

## Entry Points

- `<API/RPC/event/job/webhook/admin tool>`

## Trust Boundaries

```text
<caller> -> <boundary> -> <backend> -> <data/external systems>
```

## Threats

| Threat     | Impact     | Mitigation     |
| ---------- | ---------- | -------------- |
| `<threat>` | `<impact>` | `<mitigation>` |

## Abuse Cases

- `<abuse case>`

## Required Controls

- `<control>`

## Security Validation

- `<test/review/scanner/manual approval>`
