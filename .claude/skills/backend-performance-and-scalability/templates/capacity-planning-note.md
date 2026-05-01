# Capacity Planning Note

## Scope

`<service/API/job/workflow>`

## Demand Assumptions

| Input           |     Value | Source     |
| --------------- | --------: | ---------- |
| Average traffic | `<value>` | `<source>` |
| Peak traffic    | `<value>` | `<source>` |
| Data volume     | `<value>` | `<source>` |
| Growth rate     | `<value>` | `<source>` |

## Resource Model

| Resource                | Current Capacity | Saturation Signal | Risk     |
| ----------------------- | ---------------- | ----------------- | -------- |
| CPU                     | `<capacity>`     | `<signal>`        | `<risk>` |
| Memory                  | `<capacity>`     | `<signal>`        | `<risk>` |
| DB connections          | `<capacity>`     | `<signal>`        | `<risk>` |
| External provider quota | `<capacity>`     | `<signal>`        | `<risk>` |

## Headroom

`<headroom estimate or unknown>`

## Scaling Trigger

`<metric/threshold/action>`

## Unknowns

- `<unknown>`
