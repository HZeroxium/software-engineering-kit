# Backend API and Data Flow

## Actors

- `<actor>`
- `<actor>`

## Interfaces

| Interface             | Caller     | Purpose     | Contract Owner |
| --------------------- | ---------- | ----------- | -------------- |
| `<API/RPC/event/job>` | `<caller>` | `<purpose>` | `<owner>`      |

## Request / Command Flow

```text
1. Caller sends <request/command/event>.
2. Backend validates shape and auth context.
3. Application use case loads required state.
4. Domain rules are evaluated.
5. Persistence changes are committed.
6. Side effects are emitted safely.
7. Response/event/result is returned.
```

## Data Flow

```text
Input
  -> transport validation
  -> application validation
  -> domain rules
  -> persistence
  -> side effects/events
  -> response/observable signals
```

## State Transitions

| Current State | Event / Command | Next State | Guard / Rule |
| ------------- | --------------- | ---------- | ------------ |
| `<state>`     | `<command>`     | `<state>`  | `<rule>`     |

## Idempotency

- **Required:** `<yes/no>`
- **Key:** `<idempotency key / natural key / message ID>`
- **Deduplication store:** `<where>`
- **Duplicate response behavior:** `<behavior>`

## Error and Failure Flow

| Failure     | Where Detected | Response / Handling | Retryable? |
| ----------- | -------------- | ------------------- | ---------- |
| `<failure>` | `<layer>`      | `<handling>`        | `<yes/no>` |

## Observability Points

| Step     | Metric     | Log     | Trace    |
| -------- | ---------- | ------- | -------- |
| `<step>` | `<metric>` | `<log>` | `<span>` |
