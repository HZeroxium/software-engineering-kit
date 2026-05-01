# Java Idempotent Consumer Review Example

## Scenario

A Java backend consumer handles `PaymentConfirmed` messages and updates order state.

## Finding

The consumer updates the order and sends a notification every time the message is delivered. There is no deduplication by message ID or payment ID.

## Risk

- **Severity:** Blocking if duplicate delivery is possible.
- **Failure mode:** Duplicate notifications or repeated state changes.
- **Scope:** Integration/distributed communication and domain/API correctness.

## Minimal Fix

- Add deduplication using message ID or payment ID.
- Make state transition idempotent.
- Send notification only after durable state confirms first processing.

## Validation

- Duplicate message test.
- Consumer crash/retry test if test harness supports it.
- Verify logs/metrics include duplicate detection without sensitive data.
