# Deprecation Policy

## When to Deprecate

Deprecate an artifact when:

- It duplicates another artifact.
- It is stale.
- It triggers incorrectly.
- It is too broad.
- It encourages unsafe behavior.
- It has been replaced.
- It is no longer used.

## Deprecation Before Deletion

Prefer deprecation before deletion when:

- The user may still invoke it by habit.
- Other artifacts reference it.
- It has unclear replacement.
- It affects a common workflow.

## Deprecation Note

Add a short note:

```markdown
# Deprecated

Status: Deprecated
Replacement: <artifact-name/path>
Reason:
Removal target:
```

## Delete Immediately When

- It contains secrets.
- It exposes sensitive data.
- It instructs unsafe behavior.
- It creates severe conflict with safety rules.

## Validation After Deprecation

- Confirm replacement exists.
- Confirm direct invocation of replacement works.
- Confirm old references are updated.
- Confirm no duplicate active guidance remains.
