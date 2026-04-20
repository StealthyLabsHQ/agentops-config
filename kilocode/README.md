# Kilo Code

Config files for [Kilo Code](https://kilocode.ai) — open-source AI coding agent for VS Code (fork of Roo Code / Cline lineage).

## Files

- **`.kilocode/rules/minimal.md`** — workspace rule loaded into the agent's system prompt.

## How it works

Kilo Code reads rules from:

- **Global:** configured in the Kilo Code extension settings.
- **Workspace:** `.kilocode/rules/*.md` at the repo root — all files are concatenated into the system prompt.

Because Kilo Code shares lineage with Cline and Roo Code, it also falls back to `.clinerules/` and `.roo/rules/` if `.kilocode/rules/` is absent.

## Usage

Copy the `.kilocode/` directory into the root of your target repo:

```bash
cp -r kilocode/.kilocode /path/to/your-repo/.kilocode
```

## Notes

- If you already ship `cline/.clinerules/` or `.roo/rules/` in your repo, Kilo Code will pick those up — this folder is only needed for Kilo-specific rules.
- Prefer several small rule files over one long one to keep scope tight.
- `.kilocodeignore` can be used to exclude paths from the agent's context.
