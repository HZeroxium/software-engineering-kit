# AI Evaluation

## Purpose

Measure whether AI behavior is good enough for the backend use case.

## Evaluation Types

- Offline golden-set evaluation.
- Regression evaluation.
- Retrieval evaluation.
- Groundedness/faithfulness evaluation.
- Safety evaluation.
- Human review.
- A/B or shadow evaluation.
- Production monitoring.

## Evaluation Questions

- What is the task success criterion?
- What examples represent real usage?
- What edge cases matter?
- What failures are unacceptable?
- What quality threshold gates release?
- How is drift detected?

## RAG Metrics

- Retrieval recall.
- Retrieval precision.
- Context relevance.
- Answer groundedness.
- Answer relevance.
- Citation/evidence quality.

## Failure Modes

- No evaluation before launch.
- Evaluation data not representative.
- LLM-as-judge used without calibration.
- Quality threshold undefined.
- Prompt/model changes not regression-tested.
