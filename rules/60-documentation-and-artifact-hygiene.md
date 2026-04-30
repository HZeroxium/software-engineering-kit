# Documentation and Artifact Hygiene

## Documentation Discipline

Documentation must be grounded in current source-of-truth evidence:

- Code
- Configs
- Tests
- Scripts
- APIs
- Schemas
- CI configs
- Runtime behavior
- User-provided requirements

Avoid:

- Stale claims
- Invented commands
- Invented architecture
- Invented APIs
- Idealized descriptions that do not match the repository
- Undocumented assumptions
- Duplicate or conflicting guidance

When documentation is based on assumptions, label them clearly.

## Supported Documentation Types

Support practical, copy-ready documentation such as:

- Markdown docs
- Jira-ready writeups
- Confluence-ready writeups
- Architecture notes
- ADR-style decisions
- Feature specs
- Implementation notes
- Test plans
- Troubleshooting docs
- Runbooks
- API documentation
- Release notes
- Migration notes
- AI artifact docs

## Documentation Quality Bar

Good documentation should answer:

- What is this?
- Why does it exist?
- Who uses it?
- How does it work?
- What are the inputs and outputs?
- What are the constraints?
- How is it validated?
- What can fail?
- How do we troubleshoot it?
- How do we roll it back or disable it when applicable?
- What source evidence supports it?

## Commands in Documentation

Before documenting commands:

- Discover commands from the repo.
- Verify commands when possible.
- Do not invent commands.
- State uncertainty if commands are inferred.
- Avoid documenting machine-specific commands as universal.
- Avoid documenting production-impacting commands without safety notes.

## Architecture Documentation

For architecture docs:

- Separate current architecture from proposed architecture.
- Identify module boundaries.
- Identify data flow.
- Identify API boundaries.
- Identify persistence boundaries.
- Identify operational concerns.
- Identify security boundaries.
- Identify known limitations and trade-offs.
- Avoid drawing conclusions not supported by code or requirements.

## AI Artifact Hygiene

For AI artifacts, prefer files that are:

- Small
- Focused
- Versioned
- Auditable
- Easy to disable or retire
- Clear about scope and trigger
- Clear about inputs and outputs
- Clear about permissions and prohibited actions
- Clear about validation and failure behavior

AI artifacts include:

- Global instructions
- Repo-level instructions
- Tool-specific instructions
- Prompt files
- Skills
- Custom agents
- Rules
- Workflow docs
- Security policies
- Command guards
- Hook docs
- MCP docs

## Avoid Instruction Conflicts

Avoid duplicated or conflicting instructions across:

- User-global instructions
- Repo-level instructions
- Tool-specific instructions
- Skills
- Agents
- Hooks
- MCP server docs
- Prompt files
- Team docs

When conflicts exist:

- Prefer the more specific and current source.
- Call out the conflict.
- Recommend consolidation.
- Avoid silently choosing one if the decision affects safety or correctness.

## Artifact Boundaries

Distinguish artifact types clearly:

- Instruction artifacts: guide behavior but do not enforce it.
- Executable tools: run code or commands and need tests.
- External data connectors: expose data and need scope control.
- Automation hooks: run during lifecycle events and need safety review.
- Security policies: define allowed, denied, or approval-required behavior.
- Human approval boundaries: define where automation stops.

Do not describe instruction-only files as hard enforcement.

## Update Triggers

Update documentation or AI artifacts when:

- Architecture changes.
- Build, test, lint, or deploy commands change.
- Testing strategy changes.
- CI behavior changes.
- Repeated AI failures reveal missing guidance.
- Security policy changes.
- Tool behavior changes.
- Permissions or approval boundaries change.
- Dependencies or frameworks change materially.
- API contracts or schemas change.
- Operational procedures change.
- Incidents reveal missing troubleshooting guidance.

## Maintenance

For important artifacts:

- Keep ownership clear.
- Review periodically.
- Remove stale rules.
- Merge duplicates.
- Retire low-value artifacts.
- Keep changelog notes for meaningful behavior or permission changes.
- Prefer fewer high-quality artifacts over many overlapping files.
