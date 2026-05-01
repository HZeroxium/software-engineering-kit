# Tracing Review

## Scope

`<request/workflow/integration>`

## Trace Boundaries

| Boundary                    | Span Needed? | Attributes     | Risk     |
| --------------------------- | -----------: | -------------- | -------- |
| `<API entry>`               |   `<yes/no>` | `<attributes>` | `<risk>` |
| `<DB/query>`                |   `<yes/no>` | `<attributes>` | `<risk>` |
| `<external call>`           |   `<yes/no>` | `<attributes>` | `<risk>` |
| `<message publish/consume>` |   `<yes/no>` | `<attributes>` | `<risk>` |

## Context Propagation

- **Request correlation:** `<yes/no/unknown>`
- **Async propagation:** `<yes/no/unknown>`
- **Cross-service propagation:** `<yes/no/unknown>`

## Sensitive Attribute Review

- `<attribute risk>`

## Validation

- `<trace inspection>`
- `<context propagation test/manual review>`
