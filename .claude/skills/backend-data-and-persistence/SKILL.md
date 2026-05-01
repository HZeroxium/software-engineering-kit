---
name: backend-data-and-persistence
description: Framework-agnostic backend Skill for data ownership, schema/data model design, persistence, transactions, consistency, indexing, query patterns, caching, migrations, data lifecycle, retention, deletion, privacy, and multi-tenancy.
---

# Backend Data and Persistence

Use this Skill when the task involves database design, schema, data model, queries, indexing, cache, migrations, transactions, consistency, data lifecycle, retention, deletion, or multi-tenancy.

## Purpose

Analyze and design backend data ownership, persistence, transactions, consistency, migrations, caching, query/indexing, retention, deletion, and multi-tenancy.

This Skill supports daily backend data/persistence review.

## Activation Criteria

Use when:

- Designing or reviewing persistence code.
- Adding or changing schema/data models.
- Writing or reviewing queries.
- Adding indexes.
- Designing transactions or consistency rules.
- Designing migrations.
- Adding cache behavior.
- Handling retention/deletion/privacy.
- Handling multi-tenant data isolation.

## Non-Goals

Do not:

- Assume JPA, Hibernate, Spring transactions, specific SQL dialect, NoSQL database, Redis, Kafka, or cloud database.
- Invent repository/ORM behavior.
- Recommend migrations without safety plan.
- Add caching without invalidation/correctness analysis.
- Treat persistence as only table design.

## Workflow

1. Identify data ownership boundary.
2. Identify data model/schema impact.
3. Identify read/write query patterns.
4. Analyze transaction and consistency requirements.
5. Analyze indexing and performance risks.
6. Analyze caching and invalidation if relevant.
7. Analyze migration safety.
8. Analyze retention, deletion, privacy, and multi-tenancy.
9. Define tests and validation.
10. Separate confirmed facts, assumptions, and unknowns.

## Expected Output

Return:

- Data ownership boundaries.
- Schema/data model analysis.
- Transaction and consistency requirements.
- Query/index risks.
- Cache correctness and invalidation strategy.
- Migration safety plan.
- Retention/deletion/privacy considerations.
- Multi-tenancy data isolation review.
- Test and validation strategy.

## Safety Boundaries

Require explicit approval before:

- Data deletion.
- Production migration.
- Destructive schema changes.
- Backfills on production data.
- Locking/index changes with production impact.
- Tenant isolation changes.
- Sensitive data movement.
