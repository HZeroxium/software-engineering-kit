# Audit Logging Plan

## Scope

`<security-sensitive operation>`

## Audit Events

| Event     | Actor     | Resource     | Required Fields | Sensitive Fields Excluded |
| --------- | --------- | ------------ | --------------- | ------------------------- |
| `<event>` | `<actor>` | `<resource>` | `<fields>`      | `<excluded>`              |

## Required Properties

- Actor identity.
- Resource identity.
- Action.
- Decision/result.
- Timestamp.
- Correlation/request ID.
- Source system.
- Reason or policy when applicable.
- No secrets or sensitive payloads unless explicitly approved and protected.

## Storage and Access

- **Destination:** `<audit log/store/system>`
- **Retention:** `<duration/unknown>`
- **Access control:** `<who can read>`
- **Tamper resistance:** `<control/unknown>`

## Validation

- `<test audit event emitted>`
- `<test denied action audited>`
- `<manual sensitive data review>`
