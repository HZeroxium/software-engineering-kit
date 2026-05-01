# RAG Backend Review Example

## Scenario

A backend service answers user questions using internal documents retrieved from a vector index.

## Review Summary

- **Risk level:** High.
- **Primary risks:** Unauthorized retrieval, stale context, prompt injection in documents, hallucinated answers, missing evaluation.
- **Recommendation:** Do not launch until retrieval authorization, evaluation, and monitoring are defined.

## Findings

### Blocking — Retrieval Authorization Is Unclear

- **Why it matters:** Users may retrieve documents they are not authorized to access.
- **Failure mode:** Cross-user or cross-tenant data leakage.
- **Minimal fix:** Apply authorization filtering before context assembly and test denied documents.
- **Validation:** Retrieval authorization tests.

### Blocking — No AI Evaluation Plan

- **Why it matters:** The system has no evidence that answers are grounded or useful.
- **Failure mode:** Hallucinated or misleading answers in production.
- **Minimal fix:** Create golden evaluation set with retrieval and answer-quality metrics.
- **Validation:** Offline evaluation threshold before release.

### Important — Prompt Injection in Retrieved Documents

- **Why it matters:** Documents may contain instructions that try to override system behavior.
- **Failure mode:** Model follows retrieved malicious instructions.
- **Minimal fix:** Delimit retrieved content as untrusted data and add prompt-injection tests.
- **Validation:** Safety evaluation cases.

## Suggested Monitoring

- Retrieval hit rate.
- Retrieval latency.
- Answer groundedness score.
- Model latency p95/p99.
- Token/cost per request.
- Provider error rate.
- Safety filter outcomes.
