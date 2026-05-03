# Java Backend Security Examples

Examples are illustrative only. Follow repository conventions.

## Object-Level Authorization

```java
public DocumentJob getJob(UserId actorId, DocumentJobId jobId) {
    DocumentJob job = documents.getRequired(jobId);

    if (!job.ownerId().equals(actorId)) {
        throw new AccessDeniedException("Actor cannot access document job");
    }

    return job;
}
```

## Safer Repository Shape

```java
public Optional<DocumentJob> findForOwner(UserId ownerId, DocumentJobId jobId) {
    // Implementation depends on persistence technology.
    return Optional.empty();
}
```

## Audit Event Sketch

```java
audit.record(new AuditEvent(
    actorId,
    "DOCUMENT_JOB_READ",
    jobId.value(),
    "ALLOWED"
));
```

## Notes

- Do not assume Spring Security.
- Do not use examples as framework code.
- Confirm existing error and audit conventions.
- Avoid logging sensitive payloads.
