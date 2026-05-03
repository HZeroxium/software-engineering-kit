---
purpose: Expand-contract migration pattern, high-risk change classification, backfill safety, production validation steps
load-when: Planning or reviewing a schema migration, backfill, or destructive change
tier: domain
see-also: []
---

# Migration Strategy

## Purpose

Change schema/data safely with minimal production risk.

## Safe Migration Pattern

```text
expand -> backfill -> switch reads/writes -> contract
```

## Questions

- Is the change backward compatible?
- Can old and new app versions run together?
- Does migration lock large tables?
- Is backfill rate-limited?
- Can migration be rolled back?
- How is success verified?

## High-Risk Changes

- Drop column/field.
- Rename column/field.
- Add non-null field without default/backfill.
- Large backfill.
- Unique constraint on dirty data.
- Index on large table.
- Data deletion.

## Validation

- Migration test.
- Compatibility test.
- Query plan check.
- Backfill dry run.
- Production monitoring.
