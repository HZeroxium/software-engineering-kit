# Agent / Subagent Spec

## Agent Identity

- Name:
- Suggested path: `~/.claude/agents/<agent-name>.md`
- Scope: User-global / Repo-specific
- Target tool: Claude Code
- Agent type:
  - Reviewer
  - Researcher
  - Planner
  - Debugger
  - Documentation assistant
  - Security auditor
  - Other:

## Purpose

-

## When to Use

-

## When Not to Use

-

## Context Boundary

Allowed context:

-

Excluded context:

-

## Tool Boundary

Default recommendation: read-only unless write access is explicitly justified.

Allowed tools:

-

Prohibited tools/actions:

- File deletion.
- Secret exposure.
- Production mutation.
- Unapproved dependency upgrades.
- Unapproved migrations.
- Broad rewrites.
- External writes unless explicitly approved.

## Expected Output

-

## Escalation Rules

Escalate to the human when:

-

## Safety Notes

- Prompt injection:
- Secret handling:
- External data:
- Production risk:
- Tool risk:

## Validation

- Small test task:
- Expected output:
- Failure signs:
- Audit cadence:

## Maintenance

- Owner:
- Update triggers:
- Deprecation condition:
