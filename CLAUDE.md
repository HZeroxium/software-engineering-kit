# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Repository Is

A curated kit of Claude Code AI artifacts — instructions, rules, subagents, and skills — designed to be dropped into a user-global `~/.claude/` directory or copied into a project's `.claude/` directory. There is no application code, no runtime, and no build/test/lint pipeline. Every file is Markdown.

These artifacts are **instruction-only**. They guide Claude's behavior but do not configure hooks, MCP servers, hard permission enforcement, or repository-specific commands. Do not describe them as enforcement.

## Repository Layout

```
.claude/
  CLAUDE.md            # Top-level instruction file. Imports rules via `@rules/...`
  rules/               # Numbered, topic-focused behavior rules (00–60)
  agents/              # Subagent definitions (one .md per agent, YAML frontmatter)
  skills/<name>/       # One folder per skill, each with SKILL.md + subfolders
```

Three artifact types, three different shapes:

- **Rules** (`.claude/rules/NN-topic.md`): Numbered ordering controls precedence/grouping (00 personal, 10 safety, 20 context, 30 workflow, 40 validation, 50 output, 60 docs). Imported into `.claude/CLAUDE.md` via `@rules/<file>.md`.
- **Agents** (`.claude/agents/<name>.md`): YAML frontmatter (`name`, `description`, `tools`, `model`, optional `permissionMode`, `maxTurns`) followed by Markdown body describing mission, when to use, when not to use, and output format.
- **Skills** (`.claude/skills/<name>/`): Each skill is a directory containing `SKILL.md` (frontmatter: `name`, `description`) plus a consistent set of subfolders:
  - `checklists/` — actionable lists used during the skill's workflow
  - `examples/` — worked examples / sample outputs
  - `references/` — deeper conceptual material the skill links to
  - `templates/` — fill-in-the-blank output formats

A skill may omit `checklists/` if it has no procedural lists, but `references/`, `templates/`, and `examples/` are conventional. Match the existing layout when adding new skills.

## Backend Skill Family

The backend skills are organized as a router + 9 specialized scopes. `backend-development-core` is the entry point — it classifies a backend task into one or more of:

1. `backend-domain-and-api-design`
2. `backend-application-architecture`
3. `backend-data-and-persistence`
4. `backend-security-and-trust`
5. `backend-integration-and-distributed-communication`
6. `backend-reliability-and-resilience`
7. `backend-performance-and-scalability`
8. `backend-observability-and-operations`
9. `backend-ai-governance-and-quality`

Two backend workflow skills (`backend-feature-design`, `backend-feature-implementation`) and one orchestration skill (`backend-review-orchestrator`) compose the specialized scopes. When editing one skill in this family, check the others for overlapping/conflicting guidance — the routing layer assumes scopes stay non-overlapping.

## Common Operations

There are no build/test/lint commands. Typical work in this repo:

- **Add a new skill**: Create `.claude/skills/<kebab-name>/SKILL.md` with frontmatter (`name`, `description`), then mirror the `checklists/` + `examples/` + `references/` + `templates/` layout used by neighboring skills (e.g. `code-review/`, `backend-feature-design/`).
- **Add a new agent**: Create `.claude/agents/<name>.md` with frontmatter (`name`, `description`, `tools`, `model`, optionally `permissionMode`, `maxTurns`). Match the prose structure of existing agents (Mission, When to use, When not to use, Allowed actions, Output format).
- **Add a new rule**: Create `.claude/rules/NN-topic.md` using a free numeric slot in the 00–60 range (or extend the range) and add a corresponding `@rules/NN-topic.md` import line in `.claude/CLAUDE.md`.
- **Validation**: There is no automated check. Validation is manual — read the diff, confirm frontmatter is well-formed, confirm cross-references between skills/agents/rules are not broken, and confirm new content does not duplicate or conflict with existing artifacts.

## Editing Conventions

- **Frontmatter is load-bearing.** Skills and agents are discovered by tooling via their `name` and `description` fields. Keep `description` specific enough to drive correct skill/agent selection (when to trigger, when not to).
- **Numbered rule files** (`00-`, `10-`, …) signal grouping and import order. Preserve the gap-of-10 pattern when inserting between existing rules.
- **Cross-references are by name, not path.** Skills reference each other by skill name (e.g. "use `backend-data-and-persistence`"), not by file path. When renaming a skill folder, grep for the old name across `.claude/` and update references.
- **Markdown only.** No code blocks need to compile, no schemas need to validate. But examples and templates inside skill folders are *consumed as text by future Claude sessions* — keep them concrete, copy-ready, and free of invented APIs/commands.
- **Do not duplicate guidance.** The user-global rules in `.claude/rules/` already cover safety, context, workflow, validation, output, and documentation hygiene. Skills should add domain-specific guidance on top, not restate the rules.

## What This Repo Is Not

- Not a runtime — there is no `package.json`, `pyproject.toml`, `Makefile`, or test runner. Do not invent build/test commands.
- Not enforcement — these files cannot block tool calls, gate commits, or restrict permissions. Treat them as guidance Claude reads, not policy a harness applies.
- Not a single project's `.claude/` — it is a *kit*. Many of these artifacts are intended to be portable across repositories.

<!-- rtk-instructions v2 -->
# RTK (Rust Token Killer) - Token-Optimized Commands

## Golden Rule

**Always prefix commands with `rtk`**. If RTK has a dedicated filter, it uses it. If not, it passes through unchanged. This means RTK is always safe to use.

**Important**: Even in command chains with `&&`, use `rtk`:
```bash
# ❌ Wrong
git add . && git commit -m "msg" && git push

# ✅ Correct
rtk git add . && rtk git commit -m "msg" && rtk git push
```

## RTK Commands by Workflow

### Build & Compile (80-90% savings)
```bash
rtk cargo build         # Cargo build output
rtk cargo check         # Cargo check output
rtk cargo clippy        # Clippy warnings grouped by file (80%)
rtk tsc                 # TypeScript errors grouped by file/code (83%)
rtk lint                # ESLint/Biome violations grouped (84%)
rtk prettier --check    # Files needing format only (70%)
rtk next build          # Next.js build with route metrics (87%)
```

### Test (60-99% savings)
```bash
rtk cargo test          # Cargo test failures only (90%)
rtk go test             # Go test failures only (90%)
rtk jest                # Jest failures only (99.5%)
rtk vitest              # Vitest failures only (99.5%)
rtk playwright test     # Playwright failures only (94%)
rtk pytest              # Python test failures only (90%)
rtk rake test           # Ruby test failures only (90%)
rtk rspec               # RSpec test failures only (60%)
rtk test <cmd>          # Generic test wrapper - failures only
```

### Git (59-80% savings)
```bash
rtk git status          # Compact status
rtk git log             # Compact log (works with all git flags)
rtk git diff            # Compact diff (80%)
rtk git show            # Compact show (80%)
rtk git add             # Ultra-compact confirmations (59%)
rtk git commit          # Ultra-compact confirmations (59%)
rtk git push            # Ultra-compact confirmations
rtk git pull            # Ultra-compact confirmations
rtk git branch          # Compact branch list
rtk git fetch           # Compact fetch
rtk git stash           # Compact stash
rtk git worktree        # Compact worktree
```

Note: Git passthrough works for ALL subcommands, even those not explicitly listed.

### GitHub (26-87% savings)
```bash
rtk gh pr view <num>    # Compact PR view (87%)
rtk gh pr checks        # Compact PR checks (79%)
rtk gh run list         # Compact workflow runs (82%)
rtk gh issue list       # Compact issue list (80%)
rtk gh api              # Compact API responses (26%)
```

### JavaScript/TypeScript Tooling (70-90% savings)
```bash
rtk pnpm list           # Compact dependency tree (70%)
rtk pnpm outdated       # Compact outdated packages (80%)
rtk pnpm install        # Compact install output (90%)
rtk npm run <script>    # Compact npm script output
rtk npx <cmd>           # Compact npx command output
rtk prisma              # Prisma without ASCII art (88%)
```

### Files & Search (60-75% savings)
```bash
rtk ls <path>           # Tree format, compact (65%)
rtk read <file>         # Code reading with filtering (60%)
rtk grep <pattern>      # Search grouped by file (75%)
rtk find <pattern>      # Find grouped by directory (70%)
```

### Analysis & Debug (70-90% savings)
```bash
rtk err <cmd>           # Filter errors only from any command
rtk log <file>          # Deduplicated logs with counts
rtk json <file>         # JSON structure without values
rtk deps                # Dependency overview
rtk env                 # Environment variables compact
rtk summary <cmd>       # Smart summary of command output
rtk diff                # Ultra-compact diffs
```

### Infrastructure (85% savings)
```bash
rtk docker ps           # Compact container list
rtk docker images       # Compact image list
rtk docker logs <c>     # Deduplicated logs
rtk kubectl get         # Compact resource list
rtk kubectl logs        # Deduplicated pod logs
```

### Network (65-70% savings)
```bash
rtk curl <url>          # Compact HTTP responses (70%)
rtk wget <url>          # Compact download output (65%)
```

### Meta Commands
```bash
rtk gain                # View token savings statistics
rtk gain --history      # View command history with savings
rtk discover            # Analyze Claude Code sessions for missed RTK usage
rtk proxy <cmd>         # Run command without filtering (for debugging)
rtk init                # Add RTK instructions to CLAUDE.md
rtk init --global       # Add RTK to ~/.claude/CLAUDE.md
```

## Token Savings Overview

| Category | Commands | Typical Savings |
|----------|----------|-----------------|
| Tests | vitest, playwright, cargo test | 90-99% |
| Build | next, tsc, lint, prettier | 70-87% |
| Git | status, log, diff, add, commit | 59-80% |
| GitHub | gh pr, gh run, gh issue | 26-87% |
| Package Managers | pnpm, npm, npx | 70-90% |
| Files | ls, read, grep, find | 60-75% |
| Infrastructure | docker, kubectl | 85% |
| Network | curl, wget | 65-70% |

Overall average: **60-90% token reduction** on common development operations.
<!-- /rtk-instructions -->