---
purpose: Source priority order and verification discipline for grounding documentation claims in code, tests, configs, and APIs
load-when: Writing or reviewing any documentation where factual accuracy matters
tier: foundational
see-also:
  - stale-doc-risk.md
---

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

Discover commands from the repository before documenting them. Do not document commands that cannot be verified. If a command is likely but unverified, label it as an assumption. For the full discovery procedure, see global rule `40-harness-engineering-and-validation.md`.
