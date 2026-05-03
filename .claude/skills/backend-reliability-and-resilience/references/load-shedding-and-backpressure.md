---
purpose: Load shedding strategies and backpressure mechanisms for protecting services under overload — request queuing, rejection policies, and priority tiers
load-when: Service is at risk of overload, queue saturation, or traffic spikes that exceed capacity
tier: domain
see-also: []
---

# Load Shedding and Backpressure

## Purpose

Protect service stability under overload by deliberately rejecting or delaying low-priority work rather than degrading for all callers.

## Load Shedding Strategies

- **Request rate limiting:** Reject requests above a threshold; return 429 with Retry-After.
- **Priority-based shedding:** Serve high-priority traffic (paying customers, critical flows) and drop low-priority traffic first.
- **Adaptive concurrency limit:** Measure in-flight request count; reject new requests when limit is reached.
- **Queue depth limit:** Cap the work queue; reject at enqueue time instead of timing out inside the queue.
- **Health-based shedding:** Shed load automatically when CPU, memory, or latency exceeds a threshold.

## Backpressure Mechanisms

- **Explicit backpressure:** Downstream signals slowdown to upstream (e.g., consumer pauses, async queue full signal).
- **Implicit backpressure:** Upstream observes latency increase or error rate and slows send rate.
- **Bounded queues:** Prefer bounded queues over unbounded — allows fail-fast instead of silent accumulation.
- **Producer-consumer rate matching:** Monitor queue depth; alert when producer consistently outpaces consumer.

## Review Questions

- Is there a maximum concurrency limit per service or per dependency?
- Does the service return a meaningful response (429, 503) when shedding load?
- Is the load shedding policy visible to callers (Retry-After header, status page)?
- Are bounded queues used, or can the queue grow unbounded under a burst?
- What work is highest priority and must not be shed?

## Failure Modes

- Unbounded queue absorbs load spike silently — latency grows until OOM.
- Rate limit applied globally, not per user — one abusive caller affects all.
- Load shedding not observable — operators cannot tell shedding is active.
- Backpressure not propagated — upstream continues sending at full rate while downstream queues.
