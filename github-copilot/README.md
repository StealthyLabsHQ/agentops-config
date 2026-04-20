# GitHub Copilot

Config files for [GitHub Copilot](https://github.com/features/copilot) — Copilot Chat and Copilot coding agent.

## Files

- **`.github/copilot-instructions.md`** — repository-wide custom instructions for Copilot Chat and Copilot coding agent.

## How it works

Copilot Chat and the Copilot coding agent automatically read `.github/copilot-instructions.md` from the repo root and inject it into the system context for every request.

Precedence / scoping:

- Repository-wide: `.github/copilot-instructions.md`.
- Path-scoped: `.github/instructions/*.instructions.md` (newer feature) — each file can declare an `applyTo` glob in its frontmatter.
- Personal: user-level custom instructions configured per-user in GitHub settings (not in the repo).

All are merged together; more specific scopes override less specific ones.

## Usage

Copy `.github/copilot-instructions.md` into the `.github/` directory of your target repo:

```bash
mkdir -p /path/to/your-repo/.github
cp github-copilot/.github/copilot-instructions.md /path/to/your-repo/.github/copilot-instructions.md
```

Commit and push the file — Copilot picks it up automatically on the next request.

## Notes

- Keep it short. Copilot counts these instructions against the chat context window.
- Works for Copilot Chat in VS Code, JetBrains, Visual Studio, and the web UI.
- Also read by the Copilot coding agent when acting on issues/PRs.
- Team members don't need to configure anything — the file ships with the repo.
