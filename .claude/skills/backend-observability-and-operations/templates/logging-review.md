# Logging Review

## Scope

`<feature/API/job/module>`

## Log Events

| Event     | Level                     | Fields     | Sensitive Data Risk |
| --------- | ------------------------- | ---------- | ------------------- |
| `<event>` | `<debug/info/warn/error>` | `<fields>` | `<risk>`            |

## Required Context

- Correlation/request ID.
- Actor or tenant only if safe and approved.
- Resource ID only if safe.
- Outcome.
- Error category.
- Duration if useful.

## Avoid Logging

- Secrets.
- Tokens.
- Passwords.
- Private keys.
- Raw sensitive payloads.
- Large request/response bodies.
- PII unless policy allows and masking exists.

## Findings

- `<finding>`

## Validation

- `<manual log review>`
- `<test log redaction if supported>`
