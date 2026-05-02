---
purpose: Example output for severity-based code review findings
load-when: Calibrating output depth or severity wording for a code review
---

# Example: Severity-Based Review

## Review Summary

Recommendation: Request changes.

Main concern: The patch creates orders and sends notifications in the same request path without safe transaction and retry behavior.

## Confirmed Facts

- The service creates an order.
- The service sends a notification after creating the order.
- Notification provider failures are caught and logged.
- No idempotency key is checked in the shown code.

## Assumptions

- Order creation may be retried by clients after timeout.
- Notifications should not duplicate for the same logical order.

## Blocking Findings

### B-1: Duplicate order and duplicate notification risk on retry

- Affected code/file/module: `OrderService#createOrder`
- Evidence: The method creates a new order on each call and sends notification after save, but does not check idempotency or duplicate client request identity.
- Why it matters: If the client times out and retries, the system may create multiple orders and send multiple notifications.
- Failure mode: Customer taps submit once, receives timeout, app retries, restaurant receives duplicate orders.
- Minimal suggested fix: Introduce or reuse an idempotency key for order creation, or enforce a business-level duplicate constraint if available.
- Test/validation: Add a regression test that submits the same logical request twice and verifies only one order and one notification are created.

## Important Findings

### I-1: Notification failure is logged without structured identifiers

- Affected code/file/module: `OrderNotificationService`
- Evidence: Log message contains only exception message.
- Why it matters: Production debugging needs safe identifiers such as order ID and restaurant ID.
- Failure mode: On provider outage, support cannot correlate failed notification attempts to orders.
- Minimal suggested fix: Add structured log fields with safe IDs and no sensitive customer data.
- Test/validation: Manual log review or unit test for error path if logging is wrapped.

## Optional Findings

### O-1: Extract notification payload construction

- Affected code/file/module: `OrderNotificationService`
- Why it matters: Payload construction may grow and is easier to test separately.
- Suggested improvement: Extract a small mapper method.
- Validation: Existing notification tests should pass.

## Remaining Risks

- Current transaction behavior was not fully reviewed because repository transaction annotations were not provided.
- Provider retry policy is unknown.
