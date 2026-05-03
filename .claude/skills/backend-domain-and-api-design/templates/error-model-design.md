# Error Model Design

## Scope

`<API/RPC/event/workflow>`

## Error Model Goals

- Stable client behavior.
- Clear business vs validation vs technical errors.
- Machine-readable error codes.
- Safe user-facing messages.
- Retryability semantics.
- No leakage of internal implementation details.

## Error Categories

| Category           | Description                              | Example     |
| ------------------ | ---------------------------------------- | ----------- |
| Validation         | Request shape or field constraint failed | `<example>` |
| Business           | Operation violates business rule         | `<example>` |
| Authorization      | Caller not allowed                       | `<example>` |
| Conflict           | State/version/idempotency conflict       | `<example>` |
| Not found          | Resource absent or hidden                | `<example>` |
| Rate limit / abuse | Quota or abuse control triggered         | `<example>` |
| Dependency         | Downstream dependency failed             | `<example>` |
| Internal           | Unexpected backend failure               | `<example>` |

## Error Contract

```text
<error response / RPC status / event failure format>
```

## Error Mapping

| Condition     | Error Code | Status Mapping | Retryable? | Log Level | Client Action |
| ------------- | ---------- | -------------- | ---------: | --------- | ------------- |
| `<condition>` | `<code>`   | `<status>`     | `<yes/no>` | `<level>` | `<action>`    |

## Sensitive Data Rules

- Do not expose secrets, stack traces, SQL, tokens, or internal class names.
- Mask sensitive identifiers when required.
- Include correlation/request ID if repo conventions support it.

## Validation

- `<contract test for error shape>`
- `<test for retryable/non-retryable error>`
- `<test for sensitive data not exposed>`
```
