# Schema Design

## Purpose

Design storage structure around access patterns, constraints, and evolution.

## Questions

- What data must be stored?
- Which fields are required?
- Which fields are unique?
- Which relationships exist?
- Which constraints enforce invariants?
- How will the schema evolve?
- What queries must be efficient?

## Relational Considerations

- Primary keys.
- Foreign keys.
- Unique constraints.
- Indexes.
- Normalization vs denormalization.
- Transaction boundaries.
- Migration compatibility.

## Document / NoSQL Considerations

- Aggregate shape.
- Partition key.
- Query model.
- Duplication.
- Consistency.
- Schema evolution.
- Hot partition risk.

## Smells

- No constraint for critical uniqueness.
- Query needs not reflected in schema.
- Required field added without migration path.
- Tenant ID missing from tenant-owned data.
- Soft delete without filtering discipline.
