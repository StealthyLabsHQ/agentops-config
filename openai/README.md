# OpenAI / Codex

Config files for [Codex](https://developers.openai.com/codex) - OpenAI's coding agent (CLI, IDE extension, web, and cloud).

## Files

- **`AGENTS.md`** - core instruction set. Minimizes tokens, scope, and output. Drop this at the root of any repo.

## How it works

Codex reads `AGENTS.md` files automatically and merges them into the working context. Codex supports a hierarchical load order:

1. `~/.codex/AGENTS.md` - user-level global rules
2. `<repo>/AGENTS.md` - project-level rules (this file)
3. Nested `AGENTS.md` in subdirectories - scoped rules for that subtree

More specific files take precedence over less specific ones.

`AGENTS.md` is also recognized by other agentic tools (Cursor, Aider, etc.), making it a portable convention.

## Usage

Copy `AGENTS.md` to the root of your target repo:

```bash
cp openai/AGENTS.md /path/to/your-repo/AGENTS.md
```

## Notes

- Keep `AGENTS.md` short. Codex performs best with tight, unambiguous rules.
- Current `AGENTS.md` also prefers short Markdown/prose, summarized noisy output, and minimal patches over full rewrites.
- Re-anchor long sessions: ask Codex to re-read `AGENTS.md` if output begins to drift.
- For monorepos, add scoped `AGENTS.md` files inside subdirectories rather than expanding the root file.
