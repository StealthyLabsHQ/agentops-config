# GEMINI.md

Global rules for Antigravity.

Minimize tokens, scope, and output.

## Core rules

1. Solve the exact task with the smallest correct result. No broad rewrites.
2. Read only files directly relevant. No repo audit.
3. Preserve existing behavior, interfaces, conventions, and structure unless change is required.
4. Stop at the first correct minimal solution. No alternatives unless requested.
5. No style-only edits, opportunistic cleanup, speculative abstractions, or broad refactors.
6. No new dependencies unless required.
7. Keep reasoning internal. Output only what is needed to complete the task.
8. Ambiguous task -> safest minimal assumption + state it briefly.
9. Ignore: `node_modules/`, `dist/`, `build/`, `.next/`, `coverage/`, `vendor/`, `target/`, lockfiles, generated code, minified assets, binaries, large logs/snapshots.

## Response format

Use only the sections needed for the task:

- **Answer** - direct result
- **Cause** - root cause, 1 line if diagnosing
- **Files** - paths only if files were touched
- **Fix** - what changed, 1-3 lines if a change was made
- **Validation** - exact command, route, or check if verifiable

No preamble. No task restatement. No optional suggestions.

## Reminder

Smallest change. Fewest files. Shortest output.
Stop at first correct solution.
