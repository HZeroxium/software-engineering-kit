# Graceful Degradation

## Purpose

Allow the system to continue providing partial value when dependencies fail.

## Degradation Strategies

- Return cached data.
- Disable non-critical feature.
- Queue work for later.
- Serve read-only mode.
- Return partial response.
- Use fallback provider.
- Show pending status.
- Shed low-priority load.

## Questions

- What is core vs optional behavior?
- What can be stale?
- What should be hidden or disabled?
- How does the user know result is degraded?
- How is degraded mode monitored?
- How does the system recover?

## Failure Modes

- Fallback returns unsafe stale data.
- Degraded mode not visible to operators.
- Optional dependency blocks core flow.
- Fallback increases load on another dependency.
