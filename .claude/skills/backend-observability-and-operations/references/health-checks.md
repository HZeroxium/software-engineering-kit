# Health Checks

## Types

- Liveness: process should be restarted if failing.
- Readiness: instance can receive traffic.
- Startup: application has initialized.

## Questions

- Does readiness check critical dependencies?
- Can dependency outage remove all instances from service?
- Is liveness too strict?
- Are checks cheap?
- Are checks safe under load?

## Failure Modes

- Liveness restarts healthy-but-slow process.
- Readiness depends on optional dependency.
- Health check hides broken critical path.
- Health check overloads dependency.
