# Artifact Lifecycle

## 1. Create

Create only when:

- Need is real.
- Trigger is clear.
- Scope is bounded.
- Maintenance owner exists.
- Simpler prompt/rule is insufficient.

## 2. Validate

Validate with:

- Direct invocation.
- Automatic activation test.
- Boundary non-activation test.
- Small representative task.
- Output quality review.
- Safety review.

## 3. Use on Small Task

Pilot on low-risk work.

Check:

- Did it activate?
- Was output useful?
- Did it follow boundaries?
- Was context overhead acceptable?

## 4. Audit

Audit after repeated use.

Look for:

- Duplicates.
- Conflicts.
- Stale guidance.
- Weak activation.
- Missing safety.
- Poor output format.

## 5. Split / Merge

Split when:

- Artifact handles unrelated workflows.
- Trigger becomes too broad.
- Supporting files are overloaded.

Merge when:

- Two artifacts have same trigger.
- Outputs overlap.
- Maintenance burden is high.

## 6. Deprecate

Deprecate when:

- Artifact is rarely used.
- Replacement exists.
- Behavior is stale.
- Scope is wrong.

## 7. Retire

Delete or archive when:

- No longer used.
- Conflicts with better artifact.
- Causes wrong behavior.
- Maintenance cost exceeds value.
