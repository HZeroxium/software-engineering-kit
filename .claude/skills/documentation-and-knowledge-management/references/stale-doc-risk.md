# Stale Documentation Risk

## High-Risk Stale Claims

Watch for documentation about:

- Build commands.
- Test commands.
- Deployment steps.
- CI/CD behavior.
- Auth and permissions.
- API contracts.
- Database schemas.
- Migrations.
- Feature flags.
- Environment variables.
- Secrets handling.
- Monitoring and alerts.
- Ownership and on-call processes.
- External integrations.

## Staleness Signals

- Docs mention files that no longer exist.
- Commands fail or are not present in package/build files.
- API examples differ from tests.
- Architecture diagrams differ from code paths.
- Feature flag names differ from config.
- Screenshots no longer match UI.
- “Temporary” notes are old.
- TODOs have no owner.
- Docs conflict with README or CI.
- Repeated AI mistakes point to missing or stale guidance.

## Mitigation

- Ground docs in source files.
- Link to source-of-truth files where appropriate.
- Prefer short docs with clear ownership.
- Remove duplicate instructions.
- Mark assumptions and open questions.
- Add last-updated date for operational docs.
- Update docs when commands, architecture, or workflows change.
