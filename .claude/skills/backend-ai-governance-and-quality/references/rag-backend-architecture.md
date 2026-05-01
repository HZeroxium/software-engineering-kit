# RAG Backend Architecture

## Purpose

Design Retrieval-Augmented Generation backend systems that are grounded, observable, evaluable, and safe.

## Core Flow

```text
user request
  -> request validation
  -> query rewriting / routing
  -> retrieval
  -> filtering / authorization
  -> reranking
  -> context assembly
  -> model generation
  -> output validation
  -> response with citations/evidence when applicable
```

## RAG Design Questions

- What corpus is indexed?
- Who is authorized to retrieve each document?
- How is data chunked?
- How is metadata used?
- What retrieval metric matters?
- How is stale or deleted data handled?
- How are citations or evidence returned?
- How is hallucination measured?
- What happens when retrieval is poor?

## RAG Risks

- Unauthorized document retrieval.
- Stale context.
- Prompt injection inside documents.
- Poor recall.
- Poor precision.
- Missing provenance.
- Overlong context.
- Sensitive data leakage.
- Evaluation gaps.

## Validation

- Retrieval recall/precision tests.
- Groundedness evaluation.
- Authorization tests.
- Stale/deleted document tests.
- Prompt injection tests.
- Latency/cost monitoring.
