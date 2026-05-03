---
purpose: Query review checklist, index design questions, performance smells — missing tenant filter, N+1, deep pagination
load-when: Reviewing or designing queries, indexes, or query performance
tier: domain
see-also: []
---

# Indexing and Query Patterns

## Purpose

Align indexes with real query patterns.

## Query Review

Check:

- Filters.
- Sorts.
- Joins.
- Grouping.
- Pagination.
- Tenant/user constraints.
- Cardinality.
- Expected volume.
- Hot paths.

## Index Design Questions

- Which predicates are selective?
- Is sort order supported?
- Is pagination efficient?
- Does the index include tenant/user boundary where needed?
- What is the write overhead?
- Can the index be added safely in production?

## Smells

- Missing tenant filter.
- Deep offset pagination.
- Sorting by unindexed field.
- N+1 queries.
- High-cardinality query without limit.
- Index added without workload justification.
