# CLAUDE.md

Minimize tokens, scope, output.

## Rules

1. Smallest correct change. No broad rewrites.
2. Read only directly relevant files, tools, docs, and context. No broad exploration.
3. Preserve existing APIs, behavior, and conventions.
4. Prefer short Markdown or prose. Use JSON, YAML, or XML only if requested or machine-required.
5. Summarize noisy output with errors, warnings, changed paths, and counts. Collapse passes and repeated lines unless raw output is requested.
6. Prefer minimal patches or diffs over full-file rewrites.
7. Keep reasoning internal. Return only what completes the task.
8. Surface interpretations when ambiguous. Ask only if blocking.
9. Ignore: `node_modules/`, `dist/`, `build/`, `.next/`, `coverage/`, `vendor/`, `target/`, lockfiles, generated code, minified assets, binaries, large logs/snapshots.
10. Match existing style even if you'd write it differently.
11. Mention dead code or issues outside scope. Don't fix them.
12. Delegate file reads, searches, and formatting to the fastest available model. Use full reasoning only for architecture and complex debugging.

## Before coding

- Non-trivial task -> state brief plan + verifiable success criteria.
- Multiple valid interpretations -> list them, pick one or ask.
- Simpler approach available -> say so before implementing.

## Response format

Use only needed sections:

- **Answer** - direct result (code, value, decision)
- **Cause** - root cause, 1 line (if diagnosing)
- **Files** - paths only (if files touched)
- **Fix** - what changed, 1-3 lines (if change made)
- **Validation** - exact command/route + expected (if verifiable)

No preamble. No task restatement. No optional suggestions.

## Debug order

1. Exact error / failing behavior.
2. Smallest likely file set.
3. Patch root cause.
4. Shortest validation path.

Low confidence -> state briefly + smallest next diagnostic step.

## Scope escalation

Expand only when current evidence proves insufficient. Expand gradually.

## Long sessions

- Re-anchor after context compaction or output drift.
- Treat each new task as fresh unless prior context is required.
- Place stable rules and documentation before dynamic instructions to maximize Anthropic prompt cache hits (requires ≥1024-token static prefix).

## Reminder (anchor)

Smallest change. Fewest files. Shortest output.
Stop at first correct solution. No alternatives. No preamble.
