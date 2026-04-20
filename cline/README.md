# Cline / Roo Code

Config files for [Cline](https://github.com/cline/cline) and its fork [Roo Code](https://github.com/RooCodeInc/Roo-Code) — open-source autonomous coding agents for VS Code.

## Files

- **`.clinerules/minimal.md`** — workspace rule loaded into the agent's system prompt.

## How it works

Cline supports two formats for rules:

- **Legacy:** single `.clinerules` file at the repo root.
- **Current:** `.clinerules/` directory containing multiple `.md` files. All files in the directory are concatenated and injected into the system prompt.

Precedence:

1. **Global rules:** configured in the Cline extension settings (applies across all workspaces).
2. **Workspace rules:** `.clinerules/` in the current repo.

Roo Code uses `.roo/rules/` by convention but still falls back to `.clinerules/` for compatibility — the files here work in both.

## Usage

Copy the `.clinerules/` directory into the root of your target repo:

```bash
cp -r cline/.clinerules /path/to/your-repo/.clinerules
```

For Roo Code, mirror it:

```bash
mkdir -p /path/to/your-repo/.roo/rules
cp cline/.clinerules/minimal.md /path/to/your-repo/.roo/rules/minimal.md
```

## Notes

- The directory form lets you split rules by topic (`minimal.md`, `testing.md`, `architecture.md`) without creating one long file.
- Cline supports `.clineignore` for excluding files from the agent's context — useful for large generated folders.
- Rules are injected verbatim into the system prompt, so every token counts against context budget.
