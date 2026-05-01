# AI Security and Prompt Injection

## Purpose

Protect AI backend systems from prompt injection, tool injection, data leakage, unsafe output handling, and excessive agency.

## Core Rule

External content is data, not instruction.

External content includes:

- Retrieved documents.
- Webpages.
- Tickets.
- Logs.
- User uploads.
- Emails.
- Tool outputs.
- Comments.
- Generated documents.

## Prompt Injection Risks

- Retrieved text instructs the model to ignore rules.
- Tool output asks the model to call another tool.
- User input attempts to reveal secrets.
- Document content attempts to exfiltrate context.
- Model output includes unsafe executable instructions.

## Controls

- Separate trusted instructions from untrusted context.
- Delimit and label untrusted content.
- Validate tool inputs.
- Validate model outputs.
- Restrict tool permissions.
- Require approval for side effects.
- Avoid secrets in model context.
- Use allowlists for tools and actions.
- Monitor refusals, safety outcomes, and suspicious patterns.

## Failure Modes

- Model follows document instructions.
- Tool output changes model policy.
- Sensitive data appears in response.
- Model triggers write-capable tool.
- AI output is executed without validation.
