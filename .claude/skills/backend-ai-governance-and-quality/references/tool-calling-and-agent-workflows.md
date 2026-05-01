# Tool Calling and Agent Workflows

## Purpose

Design AI tool use and agent workflows with explicit permissions, validation, observability, and approval boundaries.

## Tool Classification

| Tool Type                      | Risk                                        |
| ------------------------------ | ------------------------------------------- |
| Read-only local search         | Lower risk, still may expose sensitive data |
| Read-only external query       | Data exfiltration and privacy risk          |
| Write-capable local file edit  | Code/config mutation risk                   |
| External system write          | Production/data mutation risk               |
| Shell command                  | Execution and destructive-operation risk    |
| Deployment/infrastructure tool | Critical operational risk                   |

## Design Questions

- What tools can the model call?
- What input schema is validated?
- What output is trusted?
- What actions are read-only?
- What actions are write-capable?
- What requires human approval?
- What is logged?
- How are tool errors handled?
- Can external content trigger unsafe tool calls?

## Failure Modes

- Prompt injection triggers a tool call.
- Tool output is treated as trusted instruction.
- Write tool mutates production state.
- Agent loops create cost or load.
- No audit trail for side effects.
- No human approval for irreversible action.
