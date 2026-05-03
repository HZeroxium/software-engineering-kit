---
purpose: Metric type selection, label/dimension rules, cardinality risk identification, and review questions for metric design
load-when: Reviewing or designing metrics for a backend change
tier: domain
see-also: []
---

# Metrics Design and Cardinality

## Purpose

Design metrics that are useful and safe to operate.

## Common Metric Types

- Counter: monotonically increasing events.
- Gauge: current value.
- Histogram: latency/size distribution.
- Summary: client-side distribution when supported.

## Label / Dimension Rules

Prefer bounded labels:

- Operation.
- Status class.
- Error category.
- Dependency name.
- Queue name.
- Outcome.

Avoid unbounded labels:

- User ID.
- Request ID.
- Session ID.
- Email.
- Raw URL with IDs.
- Free-form exception message.
- Token.
- High-cardinality tenant/customer unless explicitly approved.

## Review Questions

- What decision does this metric support?
- What is the unit?
- Which labels are bounded?
- Can this cause cardinality explosion?
- Does it expose sensitive data?
