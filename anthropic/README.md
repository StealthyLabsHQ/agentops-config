# Anthropic / Claude Code

Config files for [Claude Code](https://docs.claude.com/en/docs/claude-code/overview) - Anthropic's official CLI.

## Files

- **`CLAUDE.md`** - core instruction set. Minimizes tokens, scope, and output. Drop this at the root of any repo.
- **`CLAUDE-ENGINEERING.md`** - optional companion. Behavioral rules for non-trivial code where correctness matters more than token cost. Load alongside `CLAUDE.md`.

## How it works

Claude Code automatically reads `CLAUDE.md` from the current working directory at session start. It is injected into the system prompt and treated as high-priority instructions.

Load order:
1. `~/.claude/CLAUDE.md` - user-level global rules
2. `<repo>/CLAUDE.md` - project-level rules (this file)
3. Nested `CLAUDE.md` files in subdirectories - scoped rules

## Usage

### Basic

Copy `CLAUDE.md` to the root of your target repo:

```bash
cp anthropic/CLAUDE.md /path/to/your-repo/CLAUDE.md
```

### With engineering companion

For production code or complex work, add both files:

```bash
cp anthropic/CLAUDE.md             /path/to/your-repo/CLAUDE.md
cp anthropic/CLAUDE-ENGINEERING.md /path/to/your-repo/CLAUDE-ENGINEERING.md
```

Reference the companion from `CLAUDE.md` using an import:

```md
@CLAUDE-ENGINEERING.md
```

Or load both files manually at session start.

## Notes

- Keep `CLAUDE.md` short. Shorter context files usually outperform longer ones for consistency and token efficiency.
- Current `CLAUDE.md` also prefers short Markdown/prose, summarized noisy output, and minimal patches over full rewrites.
- Re-anchor long sessions: ask Claude to re-read `CLAUDE.md` if output begins to drift or widen in scope.
- After `/compact`, the model may lose instruction context - re-reading `CLAUDE.md` restores it.
