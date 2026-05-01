# Capacity Planning

## Purpose

Estimate whether the system has enough capacity for expected load and growth.

## Inputs

- Current traffic.
- Peak traffic.
- Growth rate.
- Data volume.
- Resource usage.
- Dependency quotas.
- SLO targets.
- Cost constraints.

## Questions

- What saturates first?
- What is the headroom?
- What happens at peak?
- Is scaling manual or automatic?
- Are dependencies rate-limited?
- What metric triggers scaling?

## Smells

- No peak traffic estimate.
- No dependency quota awareness.
- Scaling assumes statelessness but stateful bottleneck remains.
- Capacity plan ignores database and external providers.
