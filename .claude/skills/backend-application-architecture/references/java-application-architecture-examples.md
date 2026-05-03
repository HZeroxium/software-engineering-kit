---
purpose: Java code sketches for use case, port interface, and state rule — illustrative only, not normative
load-when: Java code examples are explicitly requested to illustrate architecture concepts
tier: scenario
see-also: []
---

# Java Application Architecture Examples

Examples are illustrative only. Follow repository conventions.

## Use Case

```java
public final class ApproveOrderUseCase {
    private final OrderRepository orders;
    private final AuditLog auditLog;

    public ApprovalResult execute(ApproveOrderCommand command) {
        Order order = orders.getRequired(command.orderId());
        order.approve(command.actorId());
        orders.save(order);
        auditLog.record("ORDER_APPROVED", command.actorId(), command.orderId());
        return new ApprovalResult(order.id(), order.status());
    }
}
```

## Port

```java
public interface OrderRepository {
    Order getRequired(String orderId);
    void save(Order order);
}
```

## State Rule

```java
public void approve(String actorId) {
    if (status != OrderStatus.PENDING_APPROVAL) {
        throw new IllegalStateException("Order cannot be approved from " + status);
    }
    this.status = OrderStatus.APPROVED;
}
```

## Notes

- Error types should match repo conventions.
- Transaction handling depends on repository/framework conventions.
- Audit behavior may belong after durable state depending on requirements.
