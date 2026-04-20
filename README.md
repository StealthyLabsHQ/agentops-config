# agentops-config

Minimal configuration files and prompt templates for Claude Code and Codex, optimized for lower token usage, tighter scope, and more consistent outputs.

## Overview

`agentops-config` is a lightweight repository of instruction files and prompt templates designed to make agentic coding sessions more efficient.

The goal is simple:
- reduce token usage
- keep task scope narrow
- avoid output drift
- encourage minimal, reliable results

This repo is especially useful if you work with:
- `CLAUDE.md` for Claude Code
- `AGENTS.md` for Codex
- reusable prompt templates for debugging, implementation, analysis, and general tasks

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
- developers using Claude Code or Codex in real projects
- users who want longer sessions with lower token consumption
- teams who want more consistent model behavior across repositories
- anyone who prefers short, practical, execution-focused outputs

## What is included

Planned structure:

```text
/claude/
  CLAUDE.md
  CLAUDE-strict.md
  CLAUDE-balanced.md

/codex/
  AGENTS.md
  AGENTS-strict.md
  AGENTS-balanced.md

/prompts/
  prompts.md

/README.md
```

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

## Recommended workflow

1. Start with a compact root instruction file.
2. Keep project-wide rules short and stable.
3. Use prompt templates for task-specific guidance.
4. Reset or re-anchor long sessions when the model begins to drift.
5. Add stricter variants only when needed.

## Philosophy

A good agent config should not try to be smart for the model.
It should make the model easier to control.

That usually means:
- fewer words
- clearer rules
- stronger boundaries
- less room for optional behavior

In practice, shorter instruction files often outperform longer “helpful” ones when the goal is consistency and token efficiency.

## Roadmap

Planned additions:
- strict and balanced variants for Claude Code
- strict and balanced variants for Codex
- reusable prompt packs
- task-specific templates
- examples for personal and team workflows

## Contributing

Contributions are welcome if they keep the repo aligned with its purpose:
- compact
- practical
- low-token
- easy to reuse

Prefer improvements that reduce ambiguity without making the files significantly longer.

## License

MIT
