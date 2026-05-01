# Metrics Review

## Scope

`<feature/API/job/service>`

## Metric Concepts

| Concept      | Type          | Unit           | Labels     | Cardinality Risk |
| ------------ | ------------- | -------------- | ---------- | ---------------- |
| `<requests>` | `<counter>`   | `<count>`      | `<labels>` | `<risk>`         |
| `<duration>` | `<histogram>` | `<seconds/ms>` | `<labels>` | `<risk>`         |
| `<errors>`   | `<counter>`   | `<count>`      | `<labels>` | `<risk>`         |
| `<backlog>`  | `<gauge>`     | `<items>`      | `<labels>` | `<risk>`         |

## Label Review

| Label     |   Bounded? | Risk     |
| --------- | ---------: | -------- |
| `<label>` | `<yes/no>` | `<risk>` |

## High-Cardinality Avoid List

- User ID.
- Request ID.
- Session ID.
- Raw URL with IDs.
- Email.
- Token.
- Free-form error message.
- Unbounded tenant/customer labels unless explicitly approved.

## Validation

- `<metrics emitted test/manual review>`
- `<dashboard query review>`
- `<cardinality review>`
