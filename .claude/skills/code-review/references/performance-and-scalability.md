# Performance and Scalability Review

## Data Access

Check:

- N+1 queries.
- Missing pagination.
- Missing limits.
- Unbounded result sets.
- Inefficient joins.
- Missing indexes.
- Query filters that cannot use indexes.
- Loading full entities when projections are enough.
- Repeated queries inside loops.
- Transaction scope too broad.

## CPU and Memory

Check:

- Inefficient algorithms.
- Repeated serialization/deserialization.
- Excessive allocation.
- Large in-memory collections.
- Unbounded buffering.
- Expensive regex.
- Blocking compression/encryption in latency-sensitive paths.
- Large object retention.

## I/O and Network

Check:

- Sequential external calls that could be batched.
- Missing batching.
- Missing connection pooling.
- Blocking calls in async/event-loop paths.
- Chatty APIs.
- Large payloads.
- Missing streaming for large data.
- Missing timeout and backpressure.

## Scalability

Check:

- Work scales linearly or worse with data size.
- Hot keys.
- Lock contention.
- Global synchronization.
- High-cardinality metrics.
- Unbounded queues.
- Expensive operations on request path.
- Lack of rate limits on expensive endpoints.

## Review Output

For each finding:

- Identify scaling dimension.
- Explain when it becomes a problem.
- Suggest minimal mitigation.
- Suggest measurement or benchmark.
- Avoid premature optimization when risk is low.
