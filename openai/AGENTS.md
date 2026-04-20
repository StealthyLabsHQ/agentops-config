# AGENTS.md

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

- After context compaction or summary, re-read this file before next action.
- Output lengthening or scope widening -> stop and re-anchor to Core rules.
- New task in same session -> treat as fresh. Smallest scope. Minimum files.
- Do not carry context from prior tasks unless required.

## Reminder (anchor)

Smallest change. Fewest files. Shortest output.
Stop at first correct solution. No alternatives. No preamble.
