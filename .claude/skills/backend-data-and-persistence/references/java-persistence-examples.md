# Java Persistence Examples

Examples are illustrative only. Follow repository conventions.

## Repository Port

```java
public interface DocumentJobRepository {
    Optional<DocumentJob> findById(DocumentJobId id);
    Optional<DocumentJob> findByOwnerAndId(UserId ownerId, DocumentJobId id);
    void save(DocumentJob job);
}
```

## Tenant-Safe Query Shape

```java
public Optional<DocumentJob> findForOwner(UserId ownerId, DocumentJobId jobId) {
    // Implementation depends on repository/DB technology.
    // The key point is that owner/tenant boundary is part of lookup.
    return Optional.empty();
}
```

## Idempotency Constraint Concept

```text
unique(owner_id, idempotency_key)
```

## Notes

- Do not assume JPA/Hibernate annotations.
- Confirm transaction behavior from repo code/config.
- Prefer existing repository and test conventions.
