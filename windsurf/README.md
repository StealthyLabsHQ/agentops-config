# Windsurf

Config files for [Windsurf](https://windsurf.com) (Codeium) — agentic IDE built around Cascade.

## Files

- **`.windsurf/rules/minimal.md`** — workspace rule loaded into Cascade's context.

## How it works

Windsurf supports two rule locations:

- **Global:** `~/.codeium/windsurf/memories/global_rules.md` — applies across all workspaces.
- **Workspace:** `.windsurf/rules/*.md` at the repo root — scoped to the project.

Legacy single-file `.windsurfrules` at the repo root is also read for backward compatibility, but the `.windsurf/rules/` directory is preferred.

Cascade merges global and workspace rules into the prompt for every turn.

## Usage

Copy the `.windsurf/` directory into the root of your target repo:

```bash
cp -r windsurf/.windsurf /path/to/your-repo/.windsurf
```

Or install globally:

```bash
mkdir -p ~/.codeium/windsurf/memories
cp windsurf/.windsurf/rules/minimal.md ~/.codeium/windsurf/memories/global_rules.md
```

## Notes

- Keep rules short. Windsurf respects token budgets, but long rules still eat context.
- You can split rules across multiple files in `.windsurf/rules/` — useful for per-language conventions.
- Cascade memories (conversational facts the agent picks up) live alongside rules — don't confuse them.
