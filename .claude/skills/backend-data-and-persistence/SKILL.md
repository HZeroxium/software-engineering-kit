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

## Required Inputs

Provide as many of the following as are available:

- Persistence code (repository, DAO, query methods, ORM config)
- Schema or data model files (DDL, migration files, entity definitions)
- Query or repository method signatures being added or reviewed
- Cache configuration or caching code if cache analysis is in scope
- Transaction configuration or framework transaction annotations
- Description of data ownership context (which module/service owns the data)
- Multi-tenancy requirements if applicable
- Retention, deletion, or privacy requirements if applicable

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

## Expected Outputs

Output type: mixed

| Component | Type | Produced when |
|-----------|------|---------------|
| Data ownership and schema analysis | analysis | Data model or schema review |
| Transaction and consistency requirements | analysis | Transaction or consistency review |
| Query/index findings | report | Query or indexing review |
| Migration safety plan | plan | Schema migration review |
| Cache correctness analysis | analysis | Cache behavior review |
| Retention/deletion/privacy considerations | analysis | Data lifecycle review |
| Multi-tenancy data isolation review | analysis | Multi-tenant context present |
| Test and validation strategy | checklist | All tasks |

## Supporting Files

| File | Purpose |
|------|---------|
| `references/reference-index.md` | Navigation map — load first to select relevant references |
| `references/data-ownership.md` | Foundational: ownership vocabulary and failure modes |
| `references/schema-design.md` | Foundational: relational and NoSQL schema design |
| `references/transaction-and-consistency-models.md` | Foundational: consistency models, outbox, saga, idempotency |
| `references/caching-strategies.md` | Domain: caching patterns, invalidation, stampede |
| `references/indexing-and-query-patterns.md` | Domain: query review and index design |
| `references/migration-strategy.md` | Domain: expand-contract, backfill, high-risk changes |
| `references/multi-tenancy-data-isolation.md` | Domain: tenant isolation models and failure modes |
| `references/data-lifecycle-retention-deletion.md` | Domain: lifecycle, privacy, deletion safety |
| `references/java-persistence-examples.md` | Scenario: Java code snippets (load only if Java examples needed) |
| `checklists/data-architecture-checklist.md` | Full data design review checklist |
| `checklists/persistence-review-checklist.md` | Persistence code review checklist |
| `checklists/migration-checklist.md` | Migration safety checklist |
| `checklists/cache-correctness-checklist.md` | Cache correctness and invalidation checklist |
| `templates/data-design-review.md` | Output template: data design review |
| `templates/persistence-risk-analysis.md` | Output template: risk register |
| `templates/migration-safety-plan.md` | Output template: migration plan |
| `templates/cache-correctness-analysis.md` | Output template: cache analysis |
| `templates/query-and-index-review.md` | Output template: query/index review |
| `examples/java-data-persistence-review-example.md` | Worked example: Java persistence finding |

## Validation

Use the relevant checklist for each task type:
- Data design: `checklists/data-architecture-checklist.md`
- Persistence review: `checklists/persistence-review-checklist.md`
- Migration: `checklists/migration-checklist.md`
- Cache: `checklists/cache-correctness-checklist.md`

## Safety Boundaries

Require explicit approval before:

- Data deletion.
- Production migration.
- Destructive schema changes.
- Backfills on production data.
- Locking/index changes with production impact.
- Tenant isolation changes.
- Sensitive data movement.
