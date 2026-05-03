---
purpose: Phase-by-phase backend implementation workflow with entry/exit criteria, decision heuristics, and common pitfalls
load-when: Starting any backend implementation task; reviewing phase transition decisions; diagnosing implementation problems mid-task
tier: foundational
see-also:
  - test-first-or-test-aware-implementation.md
  - minimal-reviewable-diffs.md
  - backend-failure-handling-during-implementation.md
---

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

---

## Phase Entry and Exit Criteria

Use these criteria to decide when to move between phases and when to stop and escalate.

### 1. Explore

**Entry criteria:**
- You have the user's request in plain language or as acceptance criteria.
- You know which repository or module is affected.
- You have read access to the relevant source tree.

**Exit criteria:**
- You can name the specific files and modules that will change.
- You have seen at least one existing test covering nearby behavior.
- You have confirmed or documented the validation command (or marked it unknown).
- You have identified any high-risk file or approval gate.
- You have documented conventions seen in code (naming, layering, abstraction patterns).

**Heuristic:** Exploration is sufficient when you can fill in the Affected Files table in `templates/backend-implementation-plan.md` without guessing. If any row would require an assumption about a file path, class name, or validation command, explore more.

**Common pitfalls:**
- Reading only the direct target file and missing the test harness, existing error model, or internal library it depends on.
- Assuming a framework is present (Spring, FastAPI) without confirming via imports and build files.
- Accepting the first validation command found in a README without verifying it runs for this module.
- Treating a TODO comment or stale doc as authoritative evidence of current behavior.

---

### 2. Plan

**Entry criteria:**
- Explore exit criteria are met.
- You can describe the behavior change in one sentence.

**Exit criteria:**
- Every file in the plan has a stated change type (add/edit/test/doc) and a concrete reason.
- Every risk gate in `checklists/backend-risk-gate-checklist.md` has been evaluated.
- Test types are named (unit, integration, contract, etc.), not just "add tests".
- At least one validation command is listed with evidence or explicitly marked unknown.
- Any approval gate that is true is called out before editing begins.

**Heuristic:** A plan is minimal when every listed step is load-bearing — removing it would leave behavior uncovered, a test missing, or a risk unaddressed. Steps that are pure housekeeping do not belong unless the user requested them.

**Common pitfalls:**
- Planning to add tests "afterwards" for business rule or authorization changes — these should be test-first or test-concurrent.
- Including broad refactoring in the same plan as the feature change. Separate plans allow independent review and rollback.
- Listing "update docs" without specifying which doc and what changes.
- Skipping the risk gate check when the feature seems small — small features can touch security or migration boundaries.

---

### 3. Edit

**Entry criteria:**
- The plan is complete and all approval gates are either false or confirmed by the user.
- `checklists/before-backend-edit-checklist.md` passes.

**Exit criteria:**
- Every file listed in the plan has been changed.
- No file outside the plan has been changed without documenting why.
- The diff is minimal and reviewable: no unrelated formatting, no drive-by renames.
- Tests have been added or updated for every behavior change.
- Existing public contracts have not been silently altered.

**Heuristic:** If you are about to change a file not in the plan, pause and decide: is this a genuine dependency or a drive-by improvement? If the latter, note it as a follow-up and don't change it.

**Common pitfalls:**
- Changing unrelated code that "looks wrong" — widens the diff, obscures the intended change, complicates rollback.
- Editing a generated file directly instead of updating the generator or flagging the mismatch.
- Using an unfamiliar internal wrapper incorrectly by inferring behavior from its name rather than from usage and tests.
- Silently changing an error code, HTTP status, or exception type without flagging it as a public contract change.

---

### 4. Test

**Entry criteria:**
- The edit phase is complete.
- At least one validation command has been discovered or documented as unknown.

**Exit criteria:**
- Targeted tests have been run (or explicitly deferred with a stated reason).
- Build/compile/typecheck has been run or documented as not run.
- Results are recorded: command, outcome, any failures.
- If validation was not run, the reason is stated and the user is informed.

**Heuristic:** Run the smallest targeted test first. A broad suite run hides which specific assertion failed and wastes time diagnosing noise from unrelated failures.

**Common pitfalls:**
- Claiming tests pass without having run them or without the user providing test output.
- Running validation commands that were inferred rather than discovered, and presenting them as confirmed.
- Skipping validation entirely because "the change is small" — small changes can break type contracts or integration wiring silently.
- Not recording the exact command and outcome — the summary will be incomplete.

---

### 5. Fix Loop

**Entry criteria:**
- A check has failed and you have the failure output.

**Exit criteria:**
- The failing check now passes, OR
- The failure cause is unclear or implies a risk requiring user approval, and you have stopped to escalate.

**Heuristic:** Apply a fix only when all three are true: (1) the root cause is confirmed, not assumed; (2) the fix is contained to the current change scope; (3) the fix does not require changing behavior the user has not approved. If any condition is false, stop and report using the pattern in `references/backend-failure-handling-during-implementation.md`.

**Common pitfalls:**
- Applying a fix to make a test pass without verifying the test is testing the right thing — a wrong test that passes is worse than a failing test.
- Re-running a check repeatedly after applying speculative fixes without understanding the cause.
- Treating a flaky test as a fix target — mark it as a suspected flake, do not edit it to force a pass.
- Not re-running the check after a fix — a fix is not complete until the check passes.

---

### 6. Summarize

**Entry criteria:**
- Editing and validation (including any fix loop) are complete.
- All exit criteria from phases 3 and 4 are met.

**Exit criteria:**
- `checklists/backend-implementation-done-checklist.md` passes.
- The summary states what changed, why, files changed, tests added/updated, validation run/not run, and residual risks.
- Tests not run are listed with reasons.
- Follow-ups are explicitly named.

**Heuristic:** If you would mark residual risk as "none" but validation was skipped, partial, or left code paths untested, revise the risk assessment. Honest summaries prevent incidents.

**Common pitfalls:**
- Omitting tests that were not run — the summary should be explicit about validation gaps.
- Describing residual risk as "none" when validation was partial.
- Including implementation details (how it was coded) instead of behavioral claims (what it now does).
- Omitting follow-ups because they feel minor — minor gaps become incidents.
