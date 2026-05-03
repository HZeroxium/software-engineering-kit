---
purpose: RPO, RTO, MTTR, and MTBF definitions; DR planning questions; backup/restore failure modes; multi-region failover considerations
load-when: Disaster recovery, RPO/RTO targets, backup restore testing, or multi-region failover is in scope
tier: scenario
see-also:
  - reliability-availability-resilience.md
---

# Disaster Recovery, RPO, and RTO

## Definitions

- **RPO:** Maximum acceptable data loss.
- **RTO:** Maximum acceptable recovery time.

## Questions

- What data must survive disaster?
- How often are backups taken?
- Has restore been tested?
- What dependencies must be restored first?
- What manual steps exist?
- Who owns recovery?

## Failure Modes

- Backup cannot be restored.
- Restore procedure is undocumented.
- RPO/RTO mismatch business need.
- Dependencies restored in wrong order.
- Credentials unavailable during recovery.

## Additional Definitions

- **MTTR:** Mean Time to Recovery — average time from failure detection to full restoration.
- **MTBF:** Mean Time Between Failures — average operational time between incidents.
- **RTO vs MTTR:** RTO is the maximum acceptable recovery time (target); MTTR is the observed average (measure).

## Multi-Region Failover Considerations

- Is traffic routing automated or manual?
- Can the secondary region serve reads, writes, or both?
- Is data replication synchronous or asynchronous? (affects RPO)
- Are credentials, secrets, and config available independently in each region?
- Has failover to secondary and failback to primary both been tested?

## Additional Failure Modes

- Failback procedure untested — recovery from secondary to primary may cause data loss.
- Asynchronous replication lag exceeds stated RPO.
- Secondary region capacity insufficient for full primary load.
- Manual failover runbook requires unavailable personnel during an incident.
