# Event Contract Review

## Event

`<event name>`

## Event Type

- [ ] Domain event
- [ ] Integration event
- [ ] Command message
- [ ] Notification
- [ ] CDC-derived event
- [ ] Webhook callback

## Producer and Consumers

| Role     | Owner        | Notes     |
| -------- | ------------ | --------- |
| Producer | `<producer>` | `<notes>` |
| Consumer | `<consumer>` | `<notes>` |

## Event Schema

```text
<event payload/schema>
```

## Contract Review

| Concern                           | Status             | Notes     |
| --------------------------------- | ------------------ | --------- |
| Event name is a fact, not command | `<yes/no>`         | `<notes>` |
| Required fields are stable        | `<yes/no>`         | `<notes>` |
| Optional fields are compatible    | `<yes/no>`         | `<notes>` |
| Schema versioning exists          | `<yes/no/unknown>` | `<notes>` |
| Sensitive data minimized          | `<yes/no>`         | `<notes>` |
| Tenant/user context safe          | `<yes/no>`         | `<notes>` |
| Ordering assumptions clear        | `<yes/no>`         | `<notes>` |
| Duplicate delivery handled        | `<yes/no>`         | `<notes>` |

## Compatibility Risks

- `<risk>`

## Consumer Failure Handling

- `<retry/dead-letter/skip/manual recovery>`

## Validation

- `<producer contract test>`
- `<consumer contract test>`
- `<schema compatibility test>`
- `<duplicate delivery test>`
