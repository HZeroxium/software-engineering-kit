# Contract Testing

## Use Contract Tests For

- REST APIs.
- GraphQL APIs.
- gRPC APIs.
- Event schemas.
- Message payloads.
- SDK/client compatibility.
- Provider/consumer integration.

## What to Validate

- Required fields.
- Optional fields.
- Field types.
- Enum values.
- Status/error codes.
- Backward-compatible changes.
- Versioning rules.
- Unknown field behavior.
- Error response shape.
- Authentication/authorization contract when relevant.

## Provider Concerns

- Does the provider still satisfy existing consumers?
- Are removed fields or enum changes breaking?
- Are error responses stable?
- Are pagination and sorting contracts stable?

## Consumer Concerns

- Does the consumer handle optional/missing fields?
- Does the consumer tolerate backward-compatible additions?
- Does the consumer handle provider errors and timeouts?

## Avoid

- Treating contract tests as full system tests.
- Ignoring error contracts.
- Updating contracts without consumer review.
- Assuming generated clients guarantee semantic compatibility.
