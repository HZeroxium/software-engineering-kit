---
purpose: Core vocabulary — latency, throughput, p95/p99, saturation; failure modes from averaging or ignoring tail latency
load-when: Understanding or explaining core performance metrics; reviewing any latency-sensitive feature
tier: foundational
see-also:
  - database-performance.md
  - caching-performance.md
---

# Latency, Throughput, and Tail Latency

## Concepts

- **Latency:** Time to complete one request or job.
- **Throughput:** Work completed per unit time.
- **p95/p99:** Tail latency that affects worst-user experience.
- **Saturation:** Resource approaching capacity.

## Review Questions

- What is the target p95/p99?
- What is expected and peak throughput?
- Which dependency dominates latency?
- Are requests parallel or sequential?
- Is work bounded?
- Are payloads large?

## Failure Modes

- Average latency hides p99 pain.
- One slow dependency dominates request latency.
- Queueing delay ignored.
- Unbounded work per request.
- Large payload serialization cost ignored.
