# Java Distributed Communication Examples

Examples are illustrative only. Follow repository conventions and internal libraries.

## Idempotent Consumer Sketch

```java
public final class DocumentProcessedConsumer {
    private final ProcessedMessageStore processedMessages;
    private final DocumentRepository documents;

    public void handle(DocumentProcessedEvent event) {
        if (processedMessages.hasProcessed(event.messageId())) {
            return;
        }

        Document document = documents.getRequired(event.documentId());
        document.markProcessed(event.result());

        documents.save(document);
        processedMessages.markProcessed(event.messageId());
    }
}
```

## External Call Policy Sketch

```java
public record CallPolicy(
    Duration timeout,
    int maxAttempts,
    boolean idempotencyRequired
) {}
```

## Notes

- Do not assume a specific queue, RPC, or retry library.
- Confirm transaction and acknowledgement behavior from repository evidence.
- External writes require idempotency analysis.
