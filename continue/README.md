# Continue

Config files for [Continue](https://continue.dev) — open-source AI code assistant for VS Code and JetBrains.

## Files

- **`.continue/rules/minimal.md`** — workspace rule loaded into the assistant's system prompt. Uses Continue's frontmatter schema.

## How it works

Continue supports rules via:

- **Global:** `~/.continue/rules/*.md` (user-level, shared across projects).
- **Workspace:** `.continue/rules/*.md` inside the repo (versioned with the project).

Each rule file supports frontmatter:

- `name` — display name.
- `description` — used by the agent to decide when to apply.
- `alwaysApply: true` — injected into every turn.
- `globs: <pattern>` — attach only when matching files are in context.

Rules are composable — Continue merges all applicable rules into the system prompt.

## Usage

Copy the `.continue/` directory into the root of your target repo:

```bash
cp -r continue/.continue /path/to/your-repo/.continue
```

Or install globally:

```bash
mkdir -p ~/.continue/rules
cp continue/.continue/rules/minimal.md ~/.continue/rules/minimal.md
```

## Notes

- Continue also supports model and assistant config in `.continue/config.yaml` — this repo only ships rules.
- Rules support markdown includes via `@path/to/file.md`.
- Keep individual rule files focused — prefer several small ones over a single long file.
