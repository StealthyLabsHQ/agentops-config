# agentops-config-toolkit

Minimal configuration files for Claude Code, Codex, Gemini CLI, Antigravity, Cursor, Windsurf, GitHub Copilot, Aider, Cline, Continue, Zed, JetBrains Junie, Kilo Code, and Amp — optimized for lower token usage, tighter scope, and more consistent outputs.

## Overview

`agentops-config-toolkit` is a lightweight repository of instruction files designed to make agentic sessions more efficient.

The goal is simple:
- reduce token usage
- keep task scope narrow
- avoid output drift
- encourage minimal, reliable results

This repo is especially useful if you work with any agentic coding tool that reads project-level rule files — including:
- `CLAUDE.md` for Claude Code
- `AGENTS.md` for Codex and Amp
- `GEMINI.md` for Gemini CLI and Antigravity
- `.cursor/rules/*.mdc` for Cursor
- `.windsurf/rules/*.md` for Windsurf
- `.github/copilot-instructions.md` for GitHub Copilot
- `CONVENTIONS.md` for Aider
- `.clinerules/*.md` for Cline / Roo Code
- `.continue/rules/*.md` for Continue
- `.rules` for Zed
- `.junie/guidelines.md` for JetBrains Junie
- `.kilocode/rules/*.md` for Kilo Code

## Why this repo exists

Large models often become expensive or inefficient for three recurring reasons:
- they read too much context
- they explore too broadly
- they generate more output than necessary

This repo provides compact instruction files that help counter those patterns.

Instead of telling the model to do everything, these configs encourage it to:
- solve the exact task
- inspect only the minimum relevant context
- stop at the first correct solution
- avoid optional suggestions and unnecessary rewrites

## Who this is for

This repository is intended for:
- developers using any agentic coding tool (CLI, IDE-embedded, or cloud) in real projects
- users who want longer sessions with lower token consumption
- teams who want more consistent model behavior across repositories and across tools
- anyone who prefers short, practical, execution-focused outputs

## What is included

```text
/anthropic/
  CLAUDE.md
  CLAUDE-ENGINEERING.md
  README.md

/openai/
  AGENTS.md
  README.md

/google/
  gemini-cli/
    GEMINI.md
  antigravity/
    GEMINI.md
    .agents/rules/minimal.md
  README.md

/cursor/
  .cursor/rules/minimal.mdc
  README.md

/windsurf/
  .windsurf/rules/minimal.md
  README.md

/github-copilot/
  .github/copilot-instructions.md
  README.md

/aider/
  CONVENTIONS.md
  .aider.conf.yml
  README.md

/cline/
  .clinerules/minimal.md
  README.md

/continue/
  .continue/rules/minimal.md
  README.md

/zed/
  .rules
  README.md

/jetbrains/
  .junie/guidelines.md
  README.md

/kilocode/
  .kilocode/rules/minimal.md
  README.md

/amp/
  README.md

/README.md
```

### Supported tools

Each vendor folder contains the native config file(s) plus a `README.md` with tool-specific usage notes.

| Tool | Folder | Config file | Notes |
|------|--------|-------------|-------|
| Claude Code | [`anthropic/`](./anthropic/README.md) | `CLAUDE.md` (+ optional `CLAUDE-ENGINEERING.md`) | Hierarchical loading |
| Codex | [`openai/`](./openai/README.md) | `AGENTS.md` | Portable convention |
| Gemini CLI | [`google/`](./google/README.md) | `GEMINI.md` | Hierarchical loading |
| Antigravity | [`google/`](./google/README.md) | `GEMINI.md` + `.agents/rules/*.md` | Global + workspace rules |
| Cursor | [`cursor/`](./cursor/README.md) | `.cursor/rules/*.mdc` | MDC with frontmatter |
| Windsurf | [`windsurf/`](./windsurf/README.md) | `.windsurf/rules/*.md` | Also supports legacy `.windsurfrules` |
| GitHub Copilot | [`github-copilot/`](./github-copilot/README.md) | `.github/copilot-instructions.md` | Chat + coding agent |
| Aider | [`aider/`](./aider/README.md) | `CONVENTIONS.md` + `.aider.conf.yml` | Auto-loaded via config |
| Cline / Roo Code | [`cline/`](./cline/README.md) | `.clinerules/*.md` | VS Code extension |
| Continue | [`continue/`](./continue/README.md) | `.continue/rules/*.md` | VS Code + JetBrains |
| Zed | [`zed/`](./zed/README.md) | `.rules` | Reads many conventional filenames |
| JetBrains Junie | [`jetbrains/`](./jetbrains/README.md) | `.junie/guidelines.md` | IntelliJ family + AI Assistant |
| Kilo Code | [`kilocode/`](./kilocode/README.md) | `.kilocode/rules/*.md` | Fork of Roo Code |
| Amp | [`amp/`](./amp/README.md) | reuses `AGENTS.md` | No dedicated file |

## Design principles

All configs in this repo follow the same principles:

1. Smallest correct result
2. Minimum relevant scope
3. No broad exploration by default
4. No unnecessary refactors
5. No long preambles or task restatements
6. Short, structured outputs
7. Strong bias toward the first correct minimal solution

## Core use cases

These configs are built for more than just coding.

They can help with:
- bug fixing
- feature work
- code review
- repo maintenance
- writing and rewriting
- summarization
- structured analysis
- planning and decision support

## Quick start

Detailed examples below cover Claude Code, Codex, Gemini CLI, and Antigravity. For all other tools (Cursor, Windsurf, GitHub Copilot, Aider, Cline, Continue, Zed, Junie, Kilo Code, Amp), see the per-vendor `README.md` linked in the [Supported tools](#supported-tools) table above — each one documents its config location, load order, and install command.

### Claude Code

Create a `CLAUDE.md` file at the root of your repository and add a compact instruction set.

Example:

```md
# CLAUDE.md

Minimize tokens, scope, output.

## Rules

1. Smallest correct change. No broad rewrites.
2. Read only files directly relevant. No repo audit.
3. Preserve existing APIs, behavior, conventions.
4. Stop at first correct minimal solution. No alternatives.
5. No style-only edits, opportunistic cleanup, speculative abstractions.
6. No new dependencies unless required.
7. Keep reasoning internal. Output only what completes the task.
```

### Optional: CLAUDE-ENGINEERING.md

For repos where correctness matters more than token cost (production code, complex architecture), add a second file with behavioral rules derived from Andrej Karpathy's observations on LLM coding pitfalls.

Reference it from CLAUDE.md with `@CLAUDE-ENGINEERING.md` or load both files at session start.

See anthropic/CLAUDE-ENGINEERING.md for the full content.

### Codex

Create an `AGENTS.md` file at the root of your repository and use the same philosophy.

Example:

```md
# AGENTS.md

Minimize tokens, scope, and output.

## Core rules

1. Solve the exact task with the smallest correct result.
2. Read only the minimum relevant context. No broad exploration.
3. Preserve existing behavior, interfaces, conventions, and structure unless change is required.
4. Stop at the first correct minimal solution. No alternatives unless requested.
5. Keep reasoning internal. Output only what is needed to complete the task.
```

### Gemini CLI

Create a `GEMINI.md` file at the root of your repository and use the same philosophy.

Example:

```md
# GEMINI.md

Minimize tokens, scope, and output.

## Core rules

1. Solve the exact task with the smallest correct result.
2. Read only files directly relevant. No repo audit.
3. Preserve existing behavior, interfaces, conventions, and structure unless change is required.
4. Stop at the first correct minimal solution. No alternatives unless requested.
5. Keep reasoning internal. Output only what is needed to complete the task.
```

Gemini CLI notes:
- `GEMINI.md` is the default project context filename.
- Gemini CLI loads context hierarchically across global, workspace, and more specific directory context.
- You can inspect or reload active context with `/memory show` and `/memory reload`.
- You can split a large context file with `@path/to/file.md` imports.
- If needed, you can configure alternate context filenames in `.gemini/settings.json` with `context.fileName`, but this repo sticks to the default `GEMINI.md`.
- Gemini CLI also supports full system-prompt replacement with `GEMINI_SYSTEM_MD`, but this repo focuses on lightweight context files rather than full overrides.

### Google Antigravity

Antigravity supports both global and workspace-level customization.

This repo includes:
- a global rules example in `google/antigravity/GEMINI.md`
- a workspace rules example in `google/antigravity/.agents/rules/minimal.md`

Recommended usage:
- use `~/.gemini/GEMINI.md` for global rules shared across all Antigravity workspaces
- use `.agents/rules/*.md` inside a repo for versioned workspace-specific rules

Minimal workspace rule example:

```md
# Minimal Workspace Rule

- Solve the exact task with the smallest correct result.
- Read only directly relevant files. No broad repo exploration by default.
- Preserve existing behavior and structure unless change is required.
- Stop at the first correct minimal solution. No alternatives unless requested.
- Avoid style-only edits, opportunistic cleanup, and broad refactors.
- Keep output short, practical, and execution-focused.
```

Antigravity notes:
- global rules live in `~/.gemini/GEMINI.md`
- workspace rules live in `.agents/rules/` at the workspace or git root
- Antigravity still supports legacy `.agent/rules/`, but now defaults to `.agents/rules/`
- rules are plain Markdown files and support `@filename` imports
- skills live in `.agents/skills/<skill-folder>/SKILL.md` for workspace scope or `~/.gemini/antigravity/skills/<skill-folder>/` for global scope
- custom MCP servers are configured in `~/.gemini/antigravity/mcp_config.json`
- major agent behaviors such as review policy, terminal auto-execution, sandboxing, and strict mode are configured in Antigravity settings rather than in the rules files themselves

## Recommended workflow

1. Start with a compact root instruction file.
2. Keep project-wide rules short and stable.
3. Re-anchor long sessions when the model begins to drift.
4. Prefer one clean default file per tool.

## Philosophy

A good agent config should not try to be smart for the model.
It should make the model easier to control.

That usually means:
- fewer words
- clearer rules
- stronger boundaries
- less room for optional behavior

In practice, shorter instruction files often outperform longer “helpful” ones when the goal is consistency and token efficiency.

## Contributing

Contributions are welcome if they keep the repo aligned with its purpose:
- compact
- practical
- low-token
- easy to reuse

Prefer improvements that reduce ambiguity without making the files significantly longer.

## License

MIT
