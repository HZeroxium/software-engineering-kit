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
