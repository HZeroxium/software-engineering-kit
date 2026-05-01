# Performance Review

## Summary

- **Review target:** `<feature/API/query/module>`
- **Performance concern:** `<latency/throughput/resource/etc.>`
- **Evidence level:** `<measured / partial / hypothesis only>`
- **Risk level:** `<low/medium/high/critical>`

## Performance Goal

- **Latency target:** `<p50/p95/p99 or unknown>`
- **Throughput target:** `<RPS/jobs/sec/messages/sec or unknown>`
- **Resource target:** `<CPU/memory/DB/connections/cost or unknown>`

## Evidence

| Evidence                                | Source     | Interpretation     |
| --------------------------------------- | ---------- | ------------------ |
| `<metric/log/trace/query plan/profile>` | `<source>` | `<interpretation>` |

## Bottleneck Hypotheses

| Hypothesis     | Evidence     | Confidence          | Validation |
| -------------- | ------------ | ------------------- | ---------- |
| `<hypothesis>` | `<evidence>` | `<low/medium/high>` | `<test>`   |

## Risk Areas

- `<database query>`
- `<external call>`
- `<cache behavior>`
- `<concurrency/pool>`
- `<serialization>`
- `<large payload>`
- `<high cardinality>`

## Recommendations

1. `<minimal optimization>`
2. `<measurement step>`
3. `<follow-up>`

## Validation

- `<benchmark/load test/query plan/metrics/traces>`
