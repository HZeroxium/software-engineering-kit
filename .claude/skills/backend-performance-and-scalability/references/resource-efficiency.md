# Resource Efficiency

## Purpose

Use CPU, memory, IO, network, storage, and external-provider resources efficiently.

## Review Areas

- CPU-heavy loops.
- Memory allocations.
- Large payloads.
- Serialization/deserialization.
- Connection pools.
- Thread pools.
- Disk and network IO.
- External API calls.
- Logging/telemetry volume.

## Questions

- Is work proportional to request size?
- Is data streamed or loaded all at once?
- Are resources closed?
- Are pools bounded?
- Are expensive calls batched or cached safely?
- Is telemetry volume controlled?

## Failure Modes

- Memory pressure from large collections.
- Thread pool exhaustion.
- Connection leak.
- Excessive logging.
- Repeated expensive calls.
