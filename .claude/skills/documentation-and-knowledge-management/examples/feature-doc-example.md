# Example Feature Doc: Owner Order Notifications

## Overview

Owner Order Notifications sends a notification to a restaurant owner after a customer successfully places an order. The goal is to reduce time between order placement and restaurant acknowledgement.

## Status

- Status: Draft
- Owner: TBD
- Last updated: YYYY-MM-DD
- Related ticket/PR: TBD
- Source of truth: Order creation flow, notification service, notification token storage, related tests

## User-Facing Behavior

- A restaurant owner receives one notification when a new order is successfully created.
- The notification identifies the order without exposing unnecessary customer-sensitive data.
- If notification delivery fails, the order remains created and the failure is recorded for troubleshooting.

## Functional Details

### Inputs

- Order ID.
- Restaurant ID.
- Owner or restaurant notification target.
- Notification token or channel target.

### Outputs

- Notification delivery attempt.
- Delivery success/failure record if supported.
- Logs or metrics for delivery attempt.

### Business Rules

- Send notification only after order creation succeeds.
- Do not send notification if order creation fails.
- Avoid duplicate notifications for duplicate order events.
- Do not include sensitive customer data in the notification payload.

## Technical Design

### Components

| Component                    | Responsibility                                     |
| ---------------------------- | -------------------------------------------------- |
| Order service                | Owns order creation and successful order event     |
| Notification dispatcher      | Converts order event to notification request       |
| Notification provider client | Sends notification to provider                     |
| Observability                | Records delivery attempts, successes, and failures |

### Failure Handling

- Provider failure should not roll back order creation unless explicitly required.
- Retry behavior must be idempotent.
- Missing or expired notification token should be handled without crashing the order flow.

## Security and Permissions

- Do not expose private customer data in the notification.
- Verify the notification target belongs to the correct restaurant owner.
- Avoid logging full payloads if they may contain sensitive data.

## Observability

- Metric: notification attempts.
- Metric: notification successes.
- Metric: notification failures.
- Log: failed delivery with safe identifiers.
- Trace: optional if order flow is distributed.

## Testing

- Successful order sends one notification.
- Failed order sends no notification.
- Duplicate event does not duplicate notification.
- Missing token is handled safely.
- Provider failure is recorded.
- Sensitive data is excluded.

## Rollout and Rollback

- Roll out behind a feature flag if available.
- Monitor delivery failure rate and order creation latency.
- Roll back by disabling notification trigger or feature flag.

## Known Limitations

- Exact retry policy depends on provider and current queue architecture.
- Owner notification preferences are out of scope unless explicitly required.

## Open Questions

- Which notification provider/channel is required?
- What payload fields are allowed?
- Should quiet hours or mute preferences be supported?
- What is the acceptable delivery delay?
