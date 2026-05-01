# Java Backend Performance Review Example

## Scenario

A Java backend API lists document jobs and loads owner details for each job.

## Finding

The implementation performs one query for jobs and then one owner lookup per job.

## Risk

- **Severity:** Important or Blocking depending on traffic.
- **Failure mode:** N+1 query pattern causes latency and DB load to grow with page size.
- **Performance impact:** p95/p99 latency likely worsens under larger result sets.

## Evidence Needed

- Query count per request.
- p95/p99 API latency.
- DB query latency.
- Page size and traffic volume.

## Minimal Fix

- Batch-load owners by ID if existing repository conventions support it.
- Keep result size bounded.
- Add or verify indexes for list filters and sort.

## Validation

- Integration test or repository test for query behavior.
- Trace/log query count if supported.
- Load test for representative page size.
