# Java Use-Case Orchestration Example

## Scenario

Approve a pending document before it can be published.

## Orchestration

```text
1. Load document.
2. Check actor permission.
3. Validate document is in PENDING_REVIEW.
4. Transition document to APPROVED.
5. Save document.
6. Record audit event.
7. Return approved status.
```

## Java-Oriented Sketch

```java
public final class ApproveDocumentUseCase {
    private final DocumentRepository documents;
    private final PermissionChecker permissions;
    private final AuditRecorder audit;

    public ApproveDocumentResult execute(ApproveDocumentCommand command) {
        Document document = documents.getRequired(command.documentId());

        if (!permissions.canApprove(command.actorId(), document)) {
            throw new AccessDeniedException("Actor cannot approve document");
        }

        document.approve(command.actorId());
        documents.save(document);
        audit.recordDocumentApproved(command.actorId(), document.id());

        return new ApproveDocumentResult(document.id(), document.status());
    }
}
```

## Review Notes

- Authorization must be object-level.
- Transaction boundary depends on repository conventions.
- Audit durability requirements must be clarified.
- Tests should cover invalid state and unauthorized actor.
