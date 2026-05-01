# AI Agent Backend Risk Review Example

## Scenario

A backend agent can inspect support tickets, look up orders, draft responses, and optionally issue refunds.

## Review Summary

- **Risk level:** Critical if refund execution is autonomous.
- **Primary risks:** Unsafe tool side effects, prompt injection from ticket text, data leakage, missing approval record.
- **Recommendation:** Keep refund as human-approved action; allow read-only lookup and draft generation with validation.

## Findings

### Blocking — Write-Capable Tool Has No Approval Boundary

- **Why it matters:** The agent may issue refunds based on malicious or ambiguous ticket text.
- **Failure mode:** Financial loss or unauthorized action.
- **Minimal fix:** Require explicit human approval before refund execution.
- **Validation:** Test that refund tool cannot execute without approval token/decision.

### Blocking — Ticket Text Is Treated as Instruction

- **Why it matters:** A customer ticket can contain prompt injection.
- **Failure mode:** Agent ignores policy or triggers unsafe tool.
- **Minimal fix:** Treat ticket text as untrusted data; separate it from instructions.
- **Validation:** Prompt-injection safety tests.

### Important — No Audit Record for Agent Decisions

- **Why it matters:** Operators cannot reconstruct why an action was proposed.
- **Minimal fix:** Log safe audit metadata: actor, ticket ID, proposed action, approval decision, timestamp.
- **Validation:** Audit event test or manual review.

## Safer Tool Policy

| Tool             | Allowed Mode  | Approval                   |
| ---------------- | ------------- | -------------------------- |
| Ticket read      | Read-only     | Not required               |
| Order lookup     | Read-only     | Not required if authorized |
| Draft response   | Non-mutating  | Review recommended         |
| Refund execution | Write-capable | Required                   |
