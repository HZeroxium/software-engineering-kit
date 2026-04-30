# Stale Artifact Risks

## High-Risk Stale Areas

- Tool syntax.
- File locations.
- Permission behavior.
- Agent tool access behavior.
- Skill activation behavior.
- Hook behavior.
- MCP configuration.
- Build/test commands.
- Security rules.
- Project conventions.
- Repeated examples.

## Staleness Signals

- Claude repeatedly ignores or misuses an artifact.
- Skill triggers too often.
- Skill does not trigger when expected.
- Agent output is too broad.
- Agent asks for permissions unexpectedly.
- Instructions reference removed files.
- Commands fail.
- Artifacts contradict each other.
- Examples no longer match current workflow.
- User keeps correcting the same behavior.

## Mitigation

- Audit after first few uses.
- Keep core instructions short.
- Move detailed procedures into Skills.
- Version major behavior changes.
- Remove obsolete examples.
- Prefer source-of-truth links where useful.
- Use deprecation notes before deletion if user habits depend on the artifact.
