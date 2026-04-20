# Aider

Config files for [Aider](https://aider.chat) — AI pair programming in your terminal.

## Files

- **`CONVENTIONS.md`** — project conventions loaded as a read-only context file.
- **`.aider.conf.yml`** — configures Aider to auto-load `CONVENTIONS.md` on every session.

## How it works

Aider has no built-in magic filename for instructions, but it supports passing arbitrary files as read-only context via `--read`. The idiomatic pattern is:

1. Keep conventions in a dedicated file (typically `CONVENTIONS.md`).
2. Declare it in `.aider.conf.yml` so every session picks it up automatically.

Config precedence:

1. Command-line flags
2. Environment variables (`AIDER_*`)
3. `~/.aider.conf.yml` (user-level)
4. `.aider.conf.yml` (repo-level)

## Usage

Copy both files into the root of your target repo:

```bash
cp aider/CONVENTIONS.md       /path/to/your-repo/CONVENTIONS.md
cp aider/.aider.conf.yml      /path/to/your-repo/.aider.conf.yml
```

Aider will now auto-read `CONVENTIONS.md` on every run. To load ad-hoc without config:

```bash
aider --read CONVENTIONS.md
```

## Notes

- Files loaded via `read` are read-only — Aider won't propose edits to them. Use this for specs, conventions, or API references you want in context but don't want modified.
- `CONVENTIONS.md` is a community convention, not a hard requirement — any filename works.
- For multi-repo setups, consider a global `~/.aider.conf.yml` with `read:` pointing at a shared conventions file.
