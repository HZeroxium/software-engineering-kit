# Java Service Method Example

This example is illustrative and not repo-specific.

## Goal

Create an order while preserving idempotency, validation, transaction boundary, and observable failure behavior.

## Example

```java
public final class CreateOrderService {
    private final OrderRepository orderRepository;
    private final Clock clock;

    public CreateOrderService(OrderRepository orderRepository, Clock clock) {
        this.orderRepository = Objects.requireNonNull(orderRepository, "orderRepository");
        this.clock = Objects.requireNonNull(clock, "clock");
    }

    public CreateOrderResult create(CreateOrderCommand command) {
        Objects.requireNonNull(command, "command");
        validate(command);

        return orderRepository.findByIdempotencyKey(command.idempotencyKey())
                .map(existing -> CreateOrderResult.existing(existing.id()))
                .orElseGet(() -> createNewOrder(command));
    }

    private CreateOrderResult createNewOrder(CreateOrderCommand command) {
        Order order = Order.create(
                command.customerId(),
                command.restaurantId(),
                command.items(),
                command.idempotencyKey(),
                Instant.now(clock)
        );

        Order saved = orderRepository.save(order);
        return CreateOrderResult.created(saved.id());
    }

    private static void validate(CreateOrderCommand command) {
        if (command.items().isEmpty()) {
            throw new InvalidOrderException("Order must contain at least one item");
        }
    }
}
```

## Notes

- Constructor dependencies are explicit.
- Clock makes time testable.
- Idempotency is handled before creating a new order.
- Validation is explicit.
- The example does not invent transaction annotations because transaction style depends on the current repo.
- Repository/API names are illustrative placeholders.
