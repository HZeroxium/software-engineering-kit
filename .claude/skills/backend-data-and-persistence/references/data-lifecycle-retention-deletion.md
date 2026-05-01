# Data Lifecycle, Retention, and Deletion

## Purpose

Handle data from creation to deletion safely and lawfully.

## Lifecycle Questions

- When is data created?
- Who owns it?
- How long is it retained?
- Can it be archived?
- When must it be deleted?
- Is deletion hard or soft?
- Are backups affected?
- Are audit records retained separately?

## Privacy Questions

- Is data sensitive or personal?
- Is data minimized?
- Is data masked in logs and analytics?
- Are deletion requests supported?
- Are retention rules testable?

## Failure Modes

- Soft-deleted data still visible.
- Backups retain deleted sensitive data unexpectedly.
- Analytics copy not deleted.
- No owner for retention policy.
- Audit logs store sensitive payloads.
