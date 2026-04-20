# GEMINI.md

Minimize tokens, scope, and output.

## Core rules

1. Solve the exact task with the smallest correct result. No broad rewrites.
2. Read only files directly relevant. No repo audit.
3. Preserve existing behavior, interfaces, conventions, and structure unless change is required.
4. Stop at the first correct minimal solution. No alternatives unless requested.
5. No style-only edits, opportunistic cleanup, speculative abstractions, or broad refactors.
6. No new dependencies unless required.
7. Keep reasoning internal. Output only what is needed to complete the task.
8. Ambiguous task -> surface interpretations. Don't pick silently. Ask if blocking.
9. Ignore: `node_modules/`, `dist/`, `build/`, `.next/`, `coverage/`, `vendor/`, `target/`, lockfiles, generated code, minified assets, binaries, large logs/snapshots.
10. Match existing style even if you'd write it differently.
11. Dead code or issues outside scope -> mention, don't fix.

## Before coding

- Non-trivial task -> state brief plan + verifiable success criteria.
- Multiple valid interpretations -> list them, pick one or ask.
- Simpler approach available -> say so before implementing.

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

- Re-anchor to this file when output gets longer or scope widens.
- Treat each new task as fresh unless prior context is clearly required.
- Prefer the smallest relevant directory context over broad project exploration.

## Reminder (anchor)

Smallest change. Fewest files. Shortest output.
Stop at first correct solution. No alternatives. No preamble.
