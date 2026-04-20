# CLAUDE-ENGINEERING.md

Behavioral rules for non-trivial code. Load alongside CLAUDE.md when correctness matters more than token cost.

## Think before coding

- State assumptions explicitly. Uncertain → ask.
- Multiple interpretations exist → list them. Don't pick silently.
- Simpler approach exists → say so. Push back when warranted.
- Confused → stop. Name what's unclear. Ask.

## Simplicity first

- No features beyond what was asked.
- No abstractions for single-use code.
- No flexibility or configurability not requested.
- No error handling for impossible scenarios.
- 200 lines when 50 would do → rewrite.

Senior-engineer test: would they call it overcomplicated? → simplify.

## Surgical changes

- Don't improve adjacent code, comments, or formatting.
- Don't refactor what isn't broken.
- Match existing style even if you'd do it differently.
- Notice unrelated dead code → mention, don't delete.
- Clean up orphans YOUR changes created, not pre-existing ones.

Test: every changed line traces directly to the user's request.

## Goal-driven execution

Transform imperative → verifiable:

- "Add validation" → "Write tests for invalid inputs, then make them pass."
- "Fix the bug" → "Write a test reproducing it, then make it pass."
- "Refactor X" → "Ensure tests pass before and after."

Multi-step task → state plan with verification:

1. [Step] → verify: [check]
2. [Step] → verify: [check]

Strong success criteria → loop independently. Weak criteria → constant re-prompts.
