# Google / Gemini CLI & Antigravity

Config files for Google's agentic tools: [Gemini CLI](https://github.com/google-gemini/gemini-cli) and [Antigravity](https://antigravity.google).

## Structure

```text
/google/
  gemini-cli/
    GEMINI.md
  antigravity/
    GEMINI.md
    .agents/rules/minimal.md
```

## Gemini CLI

### File

- **`gemini-cli/GEMINI.md`** - core instruction set for Gemini CLI.

### How it works

Gemini CLI reads `GEMINI.md` from the current working directory at session start. Context is loaded hierarchically:

1. `~/.gemini/GEMINI.md` - global rules
2. `<repo>/GEMINI.md` - project rules (this file)
3. Nested `GEMINI.md` in subdirectories - scoped rules

Inspect or reload active context with `/memory show` and `/memory reload`.

### Usage

```bash
cp google/gemini-cli/GEMINI.md /path/to/your-repo/GEMINI.md
```

### Notes

- Split large context files with `@path/to/file.md` imports.
- Current `GEMINI.md` also prefers short Markdown/prose, summarized noisy output, and minimal patches over full rewrites.
- Alternate context filenames can be configured in `.gemini/settings.json` under `context.fileName`.
- Full system-prompt replacement is possible via the `GEMINI_SYSTEM_MD` environment variable, but this repo favors lightweight context files over full overrides.

## Antigravity

### Files

- **`antigravity/GEMINI.md`** - global rules example.
- **`antigravity/.agents/rules/minimal.md`** - workspace rules example.

### How it works

Antigravity supports both global and workspace-level customization:

- **Global rules** - `~/.gemini/GEMINI.md`, shared across all Antigravity workspaces.
- **Workspace rules** - `.agents/rules/*.md` inside a repo, versioned with the project.

Antigravity still supports legacy `.agent/rules/`, but now defaults to `.agents/rules/`.

### Usage

Global rules:

```bash
cp google/antigravity/GEMINI.md ~/.gemini/GEMINI.md
```

Workspace rules:

```bash
mkdir -p /path/to/your-repo/.agents/rules
cp google/antigravity/.agents/rules/minimal.md /path/to/your-repo/.agents/rules/minimal.md
```

### Notes

- Rules files are plain Markdown and support `@filename` imports.
- Workspace and global examples mirror the same defaults: short Markdown/prose, summarized noisy output, and minimal patches.
- Skills live in `.agents/skills/<skill-folder>/SKILL.md` for workspace scope, or `~/.gemini/antigravity/skills/<skill-folder>/` for global scope.
- Custom MCP servers are configured in `~/.gemini/antigravity/mcp_config.json`.
- Agent behaviors like review policy, terminal auto-execution, sandboxing, and strict mode are configured in Antigravity settings, not in rules files.
