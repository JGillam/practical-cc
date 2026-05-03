---
description: End-of-session cleanup — saves a handoff summary to .CLAUDE_LAST_SESSION.md so the next session can pick up where this one left off.
disable-model-invocation: true
---

We are at a good stopping point for this session. Perform the following tidy-up:

1. **Promote durable facts to memory first.** Before writing the handoff, scan this session for anything that's a *durable* user preference, project fact, feedback rule, or external reference — i.e., something still useful in *future* conversations, not just the next session. Save those to your auto-memory now. The handoff doc gets overwritten each session; memory persists. If nothing durable came up, skip this step.

2. Ensure `.CLAUDE_LAST_SESSION.md` is excluded from git by adding it to `.git/info/exclude` (check and add if missing — do NOT use `.gitignore` for this).

3. If a session summary file (`.CLAUDE_LAST_SESSION.md`) exists already, remove it.

4. Create a new session summary in `.CLAUDE_LAST_SESSION.md` (in the project root) with the following sections:

   * **Session Summary** header with today's date
   * **What was accomplished** (features added, bugs fixed, refactoring done, files changed)
   * **Current state** (what's working, what's incomplete or in-progress, known issues)
   * **Next steps** (prioritized actions for the next session)
   * **Open questions/decisions** (unresolved technical decisions, blockers, questions needing user input)

5. Let the user know the session summary has been saved and they can use `/tidydown` in their next session to load this context.
