# Minimal Workspace Rule

Use this rule to keep Antigravity sessions tight, local, and execution-focused.

- Solve the exact task with the smallest correct result.
- Read only directly relevant files, tools, docs, and context. No broad exploration.
- Preserve existing behavior, interfaces, conventions, and structure unless change is required.
- Prefer short Markdown or prose. Use JSON, YAML, or XML only if requested or machine-required.
- Summarize noisy output with errors, warnings, changed paths, and counts. Collapse passes and repeated lines unless raw output is requested.
- Prefer minimal patches or diffs over full-file rewrites.
- Stop at the first correct minimal solution. No alternatives unless requested.
- Avoid style-only edits, opportunistic cleanup, speculative abstractions, and broad refactors.
- Do not add dependencies unless they are required to complete the task.
- Keep output short, practical, and focused on completing the work.
- If the task is ambiguous, surface interpretations instead of picking silently. Ask only if blocking.
- Match existing style even if you would write it differently.
- Mention dead code or issues outside scope. Do not fix them.
- Delegate file reads, searches, and formatting to the fastest available model tier. Reserve deep reasoning for architecture and complex debugging.
- Non-trivial task: state a brief plan with verifiable success criteria before coding.
