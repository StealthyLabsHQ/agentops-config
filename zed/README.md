# Zed

Config files for [Zed](https://zed.dev) — high-performance collaborative editor with a built-in AI assistant.

## Files

- **`.rules`** — project-level rules file, auto-loaded into the Zed Agent's system prompt.

## How it works

Zed's agent looks for rules files at the repo root. It reads several conventional filenames in addition to `.rules`:

- `.rules`
- `AGENT.md` / `AGENTS.md`
- `CLAUDE.md`
- `GEMINI.md`
- `.cursorrules`
- `.windsurfrules`

This makes Zed one of the most interoperable agents — if you're already using another tool's convention, Zed will pick it up. If you want Zed-specific rules, `.rules` is the canonical choice.

Global user rules (applied across all projects) are configured via the Zed settings UI, not through a dotfile.

## Usage

Copy `.rules` into the root of your target repo:

```bash
cp zed/.rules /path/to/your-repo/.rules
```

## Notes

- Since Zed reads multiple conventional filenames, you can usually skip this folder entirely if you're already using `AGENTS.md` or `CLAUDE.md` in your repo.
- Use `.rules` when you want Zed-specific guidance that shouldn't affect other tools.
- Rules are plain Markdown with no special frontmatter or schema.
