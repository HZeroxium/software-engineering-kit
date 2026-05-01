# Backend Review Example

## Summary

- **Review target:** AI-generated Java backend diff for document processing.
- **Overall risk:** High.
- **Recommendation:** Request changes.
- **Primary scopes:** Security/trust, application architecture, data/persistence, integration/distributed communication.

## Scope Classification

| Scope                                 | Affected? | Review Focus                       |
| ------------------------------------- | --------: | ---------------------------------- |
| Domain/API                            |       Yes | Status model and error behavior    |
| Application architecture              |       Yes | Workflow and transaction boundary  |
| Data/persistence                      |       Yes | Job uniqueness and query ownership |
| Security/trust                        |       Yes | Cross-user job access              |
| Integration/distributed communication |       Yes | Async job publishing               |
| Reliability/resilience                |       Yes | Retry and duplicate handling       |
| Performance/scalability               |        No | No clear hot path yet              |
| Observability/operations              |       Yes | Job lifecycle metrics/logs         |
| AI/governance/quality                 |       Yes | AI-generated code validation       |

## Blocking Findings

### B1 — Missing Object-Level Authorization

- **Scope:** Security/trust.
- **Affected files/modules:** `DocumentStatusQueryUseCase`.
- **Why it matters:** A caller may query another user’s document job by changing `jobId`.
- **Failure mode:** Cross-user data exposure.
- **Minimal fix:** Load job and verify ownership against authenticated caller before returning status.
- **Validation:** Add test for cross-user access denial.

### B2 — Async Publish Can Be Lost After DB Commit

- **Scope:** Integration/distributed communication.
- **Affected files/modules:** `DocumentUploadUseCase`.
- **Why it matters:** If the process crashes after committing the job but before publishing work, the job remains stuck.
- **Failure mode:** Permanent `PENDING` jobs.
- **Minimal fix:** Use existing outbox/job scheduling pattern if present; otherwise document required reliable publish mechanism.
- **Validation:** Add integration test or design review for recovery path.

## Important Findings

### I1 — Missing Duplicate Request Handling

- **Scope:** Domain/API.
- **Why it matters:** Client retry after timeout can create duplicate jobs.
- **Minimal fix:** Add idempotency key or natural-key deduplication.
- **Validation:** Add retry/idempotency test.

## Optional Findings

### O1 — Improve Status Naming

- **Scope:** Domain/API.
- **Suggestion:** Prefer explicit terminal states such as `COMPLETED` and `FAILED` over generic `DONE`.
- **Rationale:** Improves API clarity.

## Minimal Fix Plan

1. Add ownership check.
2. Add idempotency behavior.
3. Use reliable publish/outbox pattern or escalate design gap.
4. Add tests for cross-user access, duplicate submission, and publish failure behavior.
5. Run repository validation command.

## Remaining Risks

- Outbox pattern depends on repository conventions.
- Validation command must be confirmed from build/CI evidence.
