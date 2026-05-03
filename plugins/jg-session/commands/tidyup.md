---
description: End-of-session cleanup — saves a handoff summary to .CLAUDE_LAST_SESSION.md so the next session can pick up where this one left off.
disable-model-invocation: true
---

We are at a good stopping point for this session. Perform the following tidy-up:

1. Ensure .CLAUDE_LAST_SESSION.md is excluded from git by adding it to .git/info/exclude (check and add if missing — do NOT use .gitignore for this)
2. If a session summary file (.CLAUDE_LAST_SESSION.md) exists already, then remove it.
3. Create a new session summary in .CLAUDE_LAST_SESSION.md (in the project root) with the following sections:

   * Session Summary header with today's date
   * What was accomplished (features added, bugs fixed, refactoring done, files changed)
   * Current state (what's working, what's incomplete or in-progress, known issues)
   * Next steps (prioritized actions for the next session)
   * Open questions/decisions (unresolved technical decisions, blockers, questions needing user input)

4. Let the user know the session summary has been saved and they can use /tidydown in their next session to load this context
