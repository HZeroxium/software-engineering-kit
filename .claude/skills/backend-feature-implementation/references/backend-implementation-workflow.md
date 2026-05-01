# Backend Implementation Workflow

## Workflow

```text
explore -> plan -> edit -> test -> fix-loop -> summarize
```

## 1. Explore

Before editing:

- Identify repository root and affected modules.
- Read existing implementation nearby.
- Read tests for existing behavior.
- Read build/test config.
- Identify internal libraries and wrappers.
- Discover validation commands from repo evidence.
- Identify high-risk files.

## 2. Plan

Before editing:

- Write minimal implementation plan.
- Identify files to change.
- Identify tests to add/update.
- Identify validation commands.
- Identify approval gates.

## 3. Edit

During editing:

- Make small focused changes.
- Preserve public contracts unless explicitly changing them.
- Reuse existing abstractions.
- Keep business logic in appropriate layer.
- Keep data access and external integration isolated where repo conventions support it.
- Add tests with the behavior change.

## 4. Test

After editing:

- Run smallest relevant tests first.
- Run broader validation if needed.
- Record commands and outcomes.
- Do not claim success without evidence.

## 5. Fix Loop

If checks fail:

- Read failure output.
- Identify root cause.
- Apply minimal fix.
- Re-run relevant check.
- Stop and escalate if failure implies unclear requirements, unsafe migration, or unknown internal behavior.

## 6. Summarize

Report:

- What changed.
- Why it changed.
- Files changed.
- Tests added/updated.
- Validation run.
- Residual risks.
- Follow-ups.
