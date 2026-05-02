---
purpose: Work breakdown template with confidence summary, uncertainty per area, and risk drivers
load-when: Estimation mode or producing an effort breakdown
---

# Estimation Breakdown

## Estimate Summary

| Confidence          | Total Estimate | Range | Main Risk Driver |
| ------------------- | -------------: | ----: | ---------------- |
| Low / Medium / High |                |       |                  |

## Assumptions

-
-

## Work Breakdown

| Area                       | Tasks | Estimate | Uncertainty     | Risk Notes |
| -------------------------- | ----- | -------: | --------------- | ---------- |
| Requirements clarification |       |          | Low/Medium/High |            |
| Backend/API                |       |          | Low/Medium/High |            |
| Frontend/UI                |       |          | Low/Medium/High |            |
| Data model/migration       |       |          | Low/Medium/High |            |
| Integration                |       |          | Low/Medium/High |            |
| Tests                      |       |          | Low/Medium/High |            |
| Observability              |       |          | Low/Medium/High |            |
| Documentation              |       |          | Low/Medium/High |            |
| Review/QA/fixes            |       |          | Low/Medium/High |            |

## Risk Drivers

- Requirement ambiguity:
- Integration unknowns:
- Data migration risk:
- Backward compatibility risk:
- Security/permission risk:
- Performance risk:
- Testing complexity:
- Operational risk:

## Estimate Confidence

High confidence when:

- Requirements are clear.
- Existing patterns are available.
- No schema/API migration is needed.
- Test harness is known.
- External dependencies are stable.

Low confidence when:

- Business rules are unclear.
- Existing architecture is unknown.
- Migration or compatibility is involved.
- External systems are involved.
- Security or production behavior is affected.

## Suggested Next Step

- Clarify:
- Spike:
- Implement:
- Defer:
