# Data Ownership

## Purpose

Define who owns data and who may read/write it.

## Ownership Questions

- Which service/module owns the data?
- Who can write the data?
- Who can read the data?
- Is the data shared by contract or by direct storage access?
- Is cross-service querying required?
- Is data duplicated? If yes, what is the source of truth?

## Good Ownership

- One clear writer.
- Explicit read models or APIs.
- Contract-based sharing.
- Clear retention/deletion responsibility.
- Auditability for sensitive data.

## Failure Modes

- Shared database without ownership.
- Multiple writers with inconsistent rules.
- Reporting queries overload source database.
- Data copied without lifecycle policy.
- Tenant isolation inconsistently applied.
