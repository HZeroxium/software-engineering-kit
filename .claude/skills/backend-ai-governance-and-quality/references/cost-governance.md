# Cost Governance

## Purpose

Make backend and AI costs visible, bounded, and owned.

## Backend Cost Drivers

- Compute.
- Database queries.
- Storage.
- Cache.
- Queue/message volume.
- Logs/metrics/traces.
- External API calls.
- Network egress.

## AI Cost Drivers

- Model tokens.
- Embeddings.
- Reranking.
- Vector database queries.
- Tool calls.
- Retries.
- Long context windows.
- LLM-as-judge evaluations.
- Human review.

## Cost Governance Questions

- What is cost per request/job/user/tenant?
- What is the expected traffic volume?
- What is the budget owner?
- What limits prevent runaway usage?
- Are retries bounded?
- Are expensive AI calls cached or avoided safely?
- Is telemetry volume controlled?
- Are cost anomalies monitored?

## Failure Modes

- AI cost grows faster than usage.
- Retry storm multiplies provider bills.
- Long prompts include unnecessary context.
- Evaluation jobs run without budget controls.
- Logs/traces store excessive payloads.
