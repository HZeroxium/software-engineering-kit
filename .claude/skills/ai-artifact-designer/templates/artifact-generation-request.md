# Artifact Generation Request

Use this prompt to generate the next artifact after design is approved.

## Prompt

```text
Generate the following AI artifact exactly as specified.

Target tool:
Target location:
Artifact type:
Artifact name:
Scope:

Purpose:
Activation criteria:
When not to use:
Required inputs:
Expected outputs:
Workflow:
Safety boundaries:
Validation:
Supporting files:
Output requirements:

Constraints:
- Do not generate hooks or MCP unless explicitly requested.
- Do not create repo-specific commands unless explicitly requested.
- Do not claim instruction artifacts enforce behavior.
- Keep default instructions concise.
- Move deep guidance into supporting files.
- Avoid duplicate/conflicting instructions.
- Prefer smallest useful artifact.
```
