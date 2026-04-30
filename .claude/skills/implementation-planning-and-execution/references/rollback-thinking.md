# Rollback Thinking

## Goal

Every meaningful change should have a disable, revert, or rollback path proportional to its risk.

## Code Rollback

Ask:

- Can this be reverted as one clean commit?
- Are unrelated changes mixed in?
- Are generated files included?
- Are public APIs changed?
- Are clients affected?

Prefer:

- Small diffs.
- Isolated commits.
- Feature flags for risky behavior.
- Backward-compatible changes.

## Data Rollback

Ask:

- Is data created, updated, deleted, or migrated?
- Is migration reversible?
- Is data loss possible?
- Is backfill idempotent?
- Can old and new code run together?
- Is dual-write or read compatibility needed?

High-risk data changes need explicit approval and manual review.

## Config Rollback

Ask:

- Which configs change?
- Are defaults safe?
- Can config be reverted without deploy?
- Is production affected?
- Are secrets involved?

## Deployment Rollback

Ask:

- Can old version run with new data?
- Can new version run with old data?
- Are API consumers backward-compatible?
- Are background jobs affected?
- Are queues/events compatible?

## Feature Disable Path

Possible disable paths:

- Feature flag.
- Config switch.
- Route disabled.
- Job disabled.
- Consumer paused.
- Roll back deployment.
- Revert commit.

## Observability During Rollback

Monitor:

- Error rate.
- Latency.
- Throughput.
- Saturation.
- Business metrics.
- Queue lag.
- Failed jobs.
- Data consistency checks.
