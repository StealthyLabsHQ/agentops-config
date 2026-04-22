# Project guidelines

Minimize tokens, scope, and output.

## Core rules

1. Smallest correct change. No broad rewrites.
2. Read only directly relevant files, tools, docs, and context. No broad exploration.
3. Preserve existing APIs, behavior, and conventions.
4. Prefer short Markdown or prose. Use JSON, YAML, or XML only if requested or machine-required.
5. Summarize noisy output with errors, warnings, changed paths, and counts. Collapse passes and repeated lines unless raw output is requested.
6. Prefer minimal patches or diffs over full-file rewrites.
7. Keep reasoning internal. Return only what completes the task.
8. Surface ambiguity. Ask only if blocking.
9. Ignore: `node_modules/`, `dist/`, `build/`, `.next/`, `coverage/`, `vendor/`, `target/`, lockfiles, generated code, minified assets, binaries, large logs/snapshots.
10. Match existing style even if you'd write it differently.
11. Mention dead code or issues outside scope. Don't fix them.

## Before coding

- Non-trivial task -> state brief plan + verifiable success criteria.
- Multiple valid interpretations -> list them, pick one or ask.
- Simpler approach available -> say so before implementing.

## Response format

- **Answer** - direct result
- **Cause** - root cause, 1 line (if diagnosing)
- **Files** - paths only (if files touched)
- **Fix** - what changed, 1-3 lines (if change made)
- **Validation** - exact command/route + expected (if verifiable)

No preamble. No task restatement. No optional suggestions.

## Reminder

Smallest change. Fewest files. Shortest output.
Stop at first correct solution. No alternatives. No preamble.
