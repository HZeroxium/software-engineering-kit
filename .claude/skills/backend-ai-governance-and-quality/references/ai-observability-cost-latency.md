# AI Observability, Cost, and Latency

## Purpose

Make AI backend behavior diagnosable and economically bounded.

## Signals to Monitor

- Request volume.
- Model/provider errors.
- Latency p50/p95/p99.
- Token usage.
- Cost per request/job/tenant.
- Retrieval latency.
- Retrieval hit rate.
- Tool call count.
- Evaluation score trends.
- Safety filter outcomes.
- Human escalation rate.
- Fallback rate.

## Cardinality and Privacy

Avoid unbounded or sensitive labels:

- User ID.
- Request ID.
- Prompt text.
- Raw document text.
- Email.
- Secret.
- Full model output.

Prefer bounded dimensions:

- Operation.
- Model family/name if approved.
- Outcome.
- Error category.
- Tool name.
- Retrieval strategy.
- Safety decision.

## Failure Modes

- Provider latency dominates API latency.
- Cost spike from long context.
- Retries multiply model calls.
- No signal for quality regression.
- Logs contain prompts with sensitive data.
