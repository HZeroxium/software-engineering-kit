# Load Test Plan

## Objective

`<what performance question this test answers>`

## Target

- **API/job/workflow:** `<target>`
- **Latency target:** `<p95/p99>`
- **Throughput target:** `<rate>`
- **Duration:** `<duration>`
- **Environment:** `<local/staging/prod-like/unknown>`

## Scenarios

| Scenario | Traffic Shape       | Expected Result |
| -------- | ------------------- | --------------- |
| Baseline | `<normal>`          | `<expected>`    |
| Stress   | `<beyond expected>` | `<expected>`    |
| Spike    | `<sudden increase>` | `<expected>`    |
| Soak     | `<long duration>`   | `<expected>`    |

## Metrics to Capture

- Latency p50/p95/p99.
- Throughput.
- Error rate.
- CPU/memory.
- DB latency and connections.
- Cache hit rate.
- Queue backlog if relevant.
- External dependency latency.
- Cost signals if available.

## Safety

- Do not run against production without approval.
- Rate-limit test traffic.
- Confirm data cleanup.
- Confirm alerts/noise handling.
