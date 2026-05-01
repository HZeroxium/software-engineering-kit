# Backend Failure Handling During Implementation

## Principle

Do not hide or hand-wave failures. Analyze them and either fix minimally or escalate.

## Failure Types

| Failure                           | Response                                            |
| --------------------------------- | --------------------------------------------------- |
| Compile/type error                | Fix directly if caused by current change            |
| Unit test failure                 | Determine whether test or implementation is wrong   |
| Integration failure               | Check environment assumptions before modifying code |
| Flaky test                        | Re-run only when justified; report suspected flake  |
| Missing command                   | Report as unknown; do not invent                    |
| Internal library behavior unclear | Stop and ask or inspect usage                       |
| Migration unsafe                  | Stop and request approval                           |
| Auth/security uncertainty         | Stop and request review                             |
| Generated code mismatch           | Find generator workflow or request approval         |

## Failure Report Pattern

```text
Failure:
<what failed>

Evidence:
<command/output/file>

Likely cause:
<cause>

Minimal fix:
<fix>

Re-run:
<command>

Escalation needed:
<yes/no and why>
```
