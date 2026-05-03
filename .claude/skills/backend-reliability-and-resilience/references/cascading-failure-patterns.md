---
purpose: Retry storm, thundering herd, head-of-line blocking, and fan-out amplification — triggers, propagation mechanics, detection signals, and mitigation
load-when: Cascading failure risk detected — service has aggressive retries, shared dependency, high fan-out, or correlated failure history
tier: scenario
see-also:
  - timeout-retry-circuit-breaker-bulkhead.md
  - load-shedding-and-backpressure.md
---

# Cascading Failure Patterns

## Purpose

Identify and mitigate patterns where a single dependency failure propagates into a wider system outage.

## Patterns

### Retry Storm

**Trigger:** Many callers retry simultaneously when a shared dependency degrades.
**Propagation:** Each retry adds load to the recovering dependency, preventing recovery.
**Mitigation:** Exponential backoff with jitter, circuit breaker, retry budget per caller.

### Thundering Herd

**Trigger:** Many callers simultaneously re-request a resource after a cache invalidation, cold start, or scheduled event.
**Propagation:** Burst load overwhelms the origin before the cache is repopulated.
**Mitigation:** Cache stampede protection (request coalescing, probabilistic early refresh, mutex on first fill).

### Head-of-Line Blocking

**Trigger:** A slow request at the head of a queue or thread pool blocks all subsequent requests.
**Propagation:** Latency increases; callers time out; load spikes; downstream dependencies are overloaded.
**Mitigation:** Timeout per request, queue depth limits, dedicated thread pools per priority tier (bulkhead).

### Fan-out Amplification

**Trigger:** A single inbound request fans out to N downstream dependencies.
**Propagation:** One slow dependency blocks the entire fan-out; error amplifies N×.
**Mitigation:** Bounded fan-out, parallel-with-timeout (not sequential), fail-fast on slow dependencies.

## Detection Signals

- Latency spike correlated with dependency degradation.
- Retry counter climbing while dependency success rate is low.
- Thread pool or connection pool saturation metrics.
- Queue depth growing during partial outage of a downstream service.

## Review Questions

- Does each caller apply jitter to retries, or are retries synchronized?
- Is there a circuit breaker to stop fan-out to a known-bad dependency?
- Is the thread/connection pool shared across multiple dependencies (shared exhaustion risk)?
- Is the fan-out bounded and parallel, or unbounded and sequential?

## Failure Modes

- Jitter implemented per instance but not across distributed callers — still synchronizes.
- Circuit breaker half-open state accepts too many probes — re-triggers collapse.
- Fan-out has no timeout — one slow dependency blocks all N responses.
- Retry budget is per-call, not per-user-request — amplifies rather than limits retries.
