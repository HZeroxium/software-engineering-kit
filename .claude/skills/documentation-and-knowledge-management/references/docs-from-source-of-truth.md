# Docs from Source of Truth

## Source Priority

Prefer evidence in this order when accuracy matters:

1. Current code.
2. Current tests.
3. Current configs.
4. Current scripts.
5. Current API specs or schema files.
6. CI configuration.
7. Runtime logs or verified behavior.
8. Existing docs.
9. Jira/issue text.
10. Stakeholder memory or assumptions.

If lower-priority sources conflict with higher-priority sources, call out the conflict.

## What to Verify

Before writing docs, verify:

- Feature behavior.
- API inputs and outputs.
- Error behavior.
- Data model and constraints.
- Migration behavior.
- Build/test commands.
- Deployment or runtime assumptions.
- Security and permission behavior.
- Observability signals.
- Known limitations.

## Current vs Proposed

Always separate:

- Current behavior.
- Proposed behavior.
- Deprecated behavior.
- Unknown behavior.
- Assumptions.

## Commands

Do not document commands unless they are discovered from:

- README.
- CONTRIBUTING docs.
- Makefile.
- package scripts.
- Maven/Gradle files.
- Python project files.
- CI configs.
- scripts directory.
- Docker/Compose files.
- Existing developer docs.

If a command is likely but unverified, label it as an assumption.

## Sensitive Information

Do not include:

- Secrets.
- Tokens.
- Passwords.
- Private keys.
- Customer data.
- Sensitive logs.
- Proprietary internal details beyond what the user approved.
