# Cursor

Config files for [Cursor](https://cursor.com) — the AI-first code editor.

## Files

- **`.cursor/rules/minimal.mdc`** — project rule using Cursor's current MDC format. Always applied to every file in the repo.

## How it works

Cursor supports two rule formats:

- **Legacy:** a single `.cursorrules` file at the repo root (deprecated but still read).
- **Current (MDC):** multiple rule files under `.cursor/rules/*.mdc`, each with frontmatter defining scope (`globs`) and activation (`alwaysApply`, `description`).

MDC rules are the recommended format. They support:

- `alwaysApply: true` — injected into every chat/agent turn.
- `globs: <pattern>` — attached only when matching files are in context.
- `description: ...` — used by the agent to decide when to pull the rule in.

Rules are composable: you can have several small rule files rather than one monolithic one.

## Usage

Copy the `.cursor/` directory into the root of your target repo:

```bash
cp -r cursor/.cursor /path/to/your-repo/.cursor
```

Or scope it differently by editing the frontmatter of `minimal.mdc`.

## Notes

- Prefer several small rules over one long file — Cursor handles composition well and it avoids pulling irrelevant context.
- Use `globs` for language- or path-specific rules (e.g. `**/*.ts`).
- If you want a rule to be manually invoked, set `alwaysApply: false` and rely on the `description` field.
