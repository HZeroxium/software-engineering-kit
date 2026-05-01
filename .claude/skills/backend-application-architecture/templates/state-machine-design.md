# State Machine Design

## Workflow

`<workflow/entity lifecycle>`

## States

| State     | Meaning     |  Terminal? |
| --------- | ----------- | ---------: |
| `<state>` | `<meaning>` | `<yes/no>` |

## Transitions

| From      | Event / Command | To        | Guard     | Side Effect |
| --------- | --------------- | --------- | --------- | ----------- |
| `<state>` | `<event>`       | `<state>` | `<guard>` | `<effect>`  |

## Invalid Transitions

| From      | Attempted Event | Expected Error |
| --------- | --------------- | -------------- |
| `<state>` | `<event>`       | `<error>`      |

## Persistence

- **State stored in:** `<table/document/aggregate/etc.>`
- **Concurrency control:** `<optimistic/pessimistic/none/unknown>`
- **Audit needed:** `<yes/no>`

## Tests

- `<valid transition test>`
- `<invalid transition test>`
- `<terminal state test>`
- `<concurrency test>`
