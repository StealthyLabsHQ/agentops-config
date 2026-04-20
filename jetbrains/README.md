# JetBrains / Junie

Config files for [Junie](https://www.jetbrains.com/junie/) — JetBrains' autonomous coding agent, and for AI Assistant project-level guidelines.

## Files

- **`.junie/guidelines.md`** — project guidelines auto-loaded by Junie and AI Assistant (newer versions).

## How it works

Junie reads `.junie/guidelines.md` from the repo root and injects it into the agent's system prompt. JetBrains AI Assistant (in recent releases) also honors the same file.

Load order:

1. IDE-level user guidelines — configured in Settings → Tools → AI Assistant / Junie.
2. Project-level guidelines — `.junie/guidelines.md` in the repo.

Project guidelines take precedence for project-specific rules but don't replace user-level ones.

## Usage

Copy the `.junie/` directory into the root of your target repo:

```bash
cp -r jetbrains/.junie /path/to/your-repo/.junie
```

## Notes

- Applies to IntelliJ IDEA, PyCharm, WebStorm, GoLand, Rider, and other JetBrains IDEs that ship Junie / AI Assistant.
- For older AI Assistant versions without Junie support, project guidelines are set via Settings → Tools → AI Assistant → Prompts and stored under `.idea/` — not via a tracked Markdown file. The `.junie/` convention is the way forward.
- Keep the file short — it's injected into every agent turn.
