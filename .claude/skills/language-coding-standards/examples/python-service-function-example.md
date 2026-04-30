# Python Service Function Example

This example is illustrative and not repo-specific.

## Goal

Classify a retryable external API failure with explicit types, timeout awareness, and safe logging.

## Example

```python
from __future__ import annotations

from dataclasses import dataclass
from typing import Protocol


@dataclass(frozen=True)
class PredictionRequest:
    text: str
    timeout_seconds: float


@dataclass(frozen=True)
class PredictionResult:
    label: str
    confidence: float


class PredictionClient(Protocol):
    async def predict(self, request: PredictionRequest) -> PredictionResult:
        ...


class PredictionService:
    def __init__(self, client: PredictionClient) -> None:
        self._client = client

    async def predict_text(self, text: str) -> PredictionResult:
        cleaned = text.strip()
        if not cleaned:
            raise ValueError("text must not be blank")

        request = PredictionRequest(text=cleaned, timeout_seconds=5.0)
        return await self._client.predict(request)
```

## Notes

- Types are explicit.
- Dataclasses are immutable value objects.
- External dependency is behind a protocol.
- Input validation occurs before external call.
- Async call is awaited.
- No retry policy is invented because retry - behavior depends on the current repo and operation idempotency.
