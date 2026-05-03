---
purpose: Java code sketches — value object, state transition enum, domain entity — illustrative only
load-when: Java code examples explicitly requested
tier: scenario
see-also: []
---

# Java Domain Modeling Examples

These examples are illustrative only. Follow repository conventions and internal libraries when available.

## Value Object

```java
public record EmailAddress(String value) {
    public EmailAddress {
        if (value == null || !value.contains("@")) {
            throw new IllegalArgumentException("Invalid email address");
        }
    }
}
```

## State Transition

```java
public enum JobStatus {
    PENDING, RUNNING, COMPLETED, FAILED;

    public boolean canTransitionTo(JobStatus next) {
        return switch (this) {
            case PENDING -> next == RUNNING || next == FAILED;
            case RUNNING -> next == COMPLETED || next == FAILED;
            case COMPLETED, FAILED -> false;
        };
    }
}
```

## Domain Entity Sketch

```java
public final class DocumentJob {
    private final String id;
    private JobStatus status;

    public void markRunning() {
        transitionTo(JobStatus.RUNNING);
    }

    public void markCompleted() {
        transitionTo(JobStatus.COMPLETED);
    }

    private void transitionTo(JobStatus next) {
        if (!status.canTransitionTo(next)) {
            throw new IllegalStateException("Invalid job status transition");
        }
        this.status = next;
    }
}
```

## Notes

- Do not copy examples blindly.
- Prefer existing repository naming and error conventions.
- Avoid framework annotations in domain model unless repo conventions require them.
