# Agent Audit Checklist

## Identity

- [ ] Agent name is clear.
- [ ] Description has specific delegation trigger.
- [ ] Purpose is narrow.
- [ ] Scope is user-global or repo-specific intentionally.

## Context Boundary

- [ ] Allowed context is clear.
- [ ] Excluded context is clear.
- [ ] Agent returns bounded summary.
- [ ] Agent does not flood main context unnecessarily.

## Tool Boundary

- [ ] Read-only by default unless write access is justified.
- [ ] Prohibited actions are listed.
- [ ] High-risk actions require escalation.
- [ ] Tool access matches role.
- [ ] No production mutation by default.

## Safety

- [ ] Prompt injection risk is addressed.
- [ ] Secret handling is addressed.
- [ ] External content is treated as untrusted.
- [ ] Human approval boundaries are clear.
- [ ] Security-sensitive work escalates.

## Output Contract

- [ ] Expected output format is clear.
- [ ] Severity or priority model exists when useful.
- [ ] Evidence vs assumption is separated.
- [ ] Validation recommendation is included.

## Maintenance

- [ ] Smoke test exists.
- [ ] Failure signs are clear.
- [ ] Deprecation condition exists.
