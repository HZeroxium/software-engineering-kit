---
purpose: API/interface style selection — REST-like, RPC, GraphQL, event, command message, webhook, internal interface trade-offs
load-when: Comparing or selecting an API/interface style
tier: domain
see-also:
  - api-contracts-versioning-and-compatibility.md
---

# API Style Selection

## Purpose

Select an interface style based on caller needs, workflow semantics, coupling, and operational risk.

## Common Styles

| Style              | Best Fit                             | Risks                                        |
| ------------------ | ------------------------------------ | -------------------------------------------- |
| REST-like HTTP     | Resource-oriented client/server APIs | CRUD bias, weak workflow semantics           |
| RPC                | Action-oriented internal operations  | Tight coupling, versioning discipline needed |
| GraphQL            | Flexible client-driven reads         | Authorization and query-cost complexity      |
| Event              | Business facts for async consumers   | Schema evolution, delivery semantics         |
| Command message    | Async work request                   | Duplicate handling, delayed feedback         |
| Webhook            | External callback                    | Authentication, replay, retries              |
| Internal interface | In-process module boundary           | Hidden coupling if boundary unclear          |

## Selection Questions

- Is the caller external, internal, or same-process?
- Is this a command or query?
- Does caller need immediate result?
- Is workflow long-running?
- Is eventual consistency acceptable?
- Are consumers known or unknown?
- What compatibility guarantees are required?

## Design Rule

Do not force every backend operation into CRUD. Workflow operations may need command-style APIs or events.
