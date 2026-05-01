# Migration Safety Plan

## Migration

`<migration summary>`

## Risk Level

`<low/medium/high/critical>`

## Change Type

- [ ] Add table/collection
- [ ] Add nullable column/field
- [ ] Add required column/field
- [ ] Rename field
- [ ] Drop field
- [ ] Backfill
- [ ] Add index
- [ ] Change constraint
- [ ] Data deletion
- [ ] Other: `<type>`

## Expand-Contract Plan

### Expand

- `<backward-compatible additive change>`

### Backfill

- `<safe backfill plan>`

### Switch

- `<application switch plan>`

### Contract

- `<remove old path after safe period>`

## Rollback Plan

- `<rollback behavior>`

## Production Safety

| Concern                | Plan     |
| ---------------------- | -------- |
| Locking                | `<plan>` |
| Runtime compatibility  | `<plan>` |
| Backfill rate limiting | `<plan>` |
| Monitoring             | `<plan>` |
| Verification           | `<plan>` |

## Validation

- `<migration test>`
- `<old app + new schema compatibility>`
- `<new app + old schema compatibility if needed>`
- `<query plan/index verification>`
