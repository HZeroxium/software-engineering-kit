---
purpose: Pagination, filtering, and sorting design — styles, filter constraints, sort safety, review smells
load-when: List API pagination, filtering, or sorting design or review
tier: domain
see-also: []
---

# Pagination, Filtering, and Sorting

## Purpose

Avoid unbounded, unstable, or expensive read APIs.

## Pagination Styles

| Style              | Use When                                | Risks                                  |
| ------------------ | --------------------------------------- | -------------------------------------- |
| Offset             | Small stable datasets, admin tools      | Slow deep pages, unstable under writes |
| Cursor             | User-facing feeds and changing datasets | Cursor design complexity               |
| Keyset             | High-volume ordered reads               | Limited arbitrary navigation           |
| Continuation token | Externalized cursor for clients         | Token compatibility and security       |

## Filtering

Check:

- Which fields can be filtered.
- Whether filters are indexed.
- Whether filters leak unauthorized data.
- Whether filter combinations are bounded.
- Whether tenant constraints are always applied.

## Sorting

Check:

- Default order.
- Stable tie-breaker.
- Index support.
- Sort fields allowed.
- Behavior under concurrent writes.

## Review Smells

- Returning all rows.
- Deep offset pagination on high-volume table.
- Sorting by unindexed field.
- Missing tenant/user filter.
- Cursor exposes internal IDs unsafely.
- Pagination order not deterministic.
