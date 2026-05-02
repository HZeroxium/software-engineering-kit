# Example: Small Bug Fix (Low Risk, Single File)

This example shows the compressed output format for a low-risk, single-file fix. Not every section of the full template is needed.

## Scenario

User: "The `calculateDiscount` method returns 0 when `quantity` is null. Fix it."

## Exploration Summary

- File: `src/main/java/com/example/pricing/DiscountService.java`
- Root cause: null check missing before arithmetic in `calculateDiscount`.
- No public API change. Single file. No migration. No config change.
- Task risk tier: **Low** — proceed directly.

## Confirmed Facts and Assumptions

- Confirmed: `quantity == null` reaches arithmetic at line 42, causing `NullPointerException`.
- Assumption: returning `0.0` for null quantity is the correct business behavior (not throwing). *Verify with the user if unclear.*

## Affected Files

| File | Reason |
|------|--------|
| `DiscountService.java` | Add null guard at line 42 |
| `DiscountServiceTest.java` | Add regression test for null quantity |

## Implementation Plan

1. Add null guard: `if (quantity == null) return 0.0;` before the arithmetic expression.
2. Add unit test: `calculateDiscount_returnsZero_whenQuantityIsNull`.

## Verification Commands

Discovered from repo:

```text
./gradlew test --tests "*.DiscountServiceTest"
```

## Implementation Summary

- Changed `DiscountService.java` line 42: added one-line null guard.
- Added 1 regression test in `DiscountServiceTest.java`.
- Tests run: `DiscountServiceTest` — 5 tests, all pass.
- Tests not run: integration suite — not relevant for a one-line null guard with no external dependency.
- Residual risk: None.
- Rollback: revert one-line change; no data or config impact.
