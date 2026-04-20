# Amp

[Amp](https://ampcode.com) — Sourcegraph's agentic coding tool (CLI, VS Code, JetBrains).

## No separate config in this repo

Amp reads `AGENTS.md` at the repo root — the same convention used by OpenAI Codex and other agentic tools.

## How it works

Amp loads `AGENTS.md` hierarchically:

1. `~/.config/AGENTS.md` — user-level global rules (varies slightly by platform).
2. `<repo>/AGENTS.md` — project-level rules.
3. Nested `AGENTS.md` in subdirectories — scoped rules.

More specific files take precedence.

## Usage

Use the file from the `openai/` folder — it already follows the `AGENTS.md` convention:

```bash
cp openai/AGENTS.md /path/to/your-repo/AGENTS.md
```

See [`openai/README.md`](../openai/README.md) for full details.

## Notes

- Keeping a single `AGENTS.md` at the repo root means Codex, Amp, Cursor (via fallback), Zed (via fallback), and others all read the same rule set — reduces maintenance.
- If you need Amp-specific rules that shouldn't affect other tools, Amp has no dedicated dotfile — use prompt-level instructions or environment config instead.
