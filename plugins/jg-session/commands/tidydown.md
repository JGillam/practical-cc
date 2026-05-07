---
description: Start-of-session context loader — reads the previous session's handoff from .CLAUDE_LAST_SESSION.md.
disable-model-invocation: true
---

Read the session summary from `.CLAUDE_LAST_SESSION.md` and use it as a **starting point — not authoritative state** — for this session.

The handoff tells you what *was* in progress and where to look, but the code, branch, and project state may have moved since it was written. Treat its claims as hypotheses to verify, not facts to act on:

- Re-read the specific files the handoff calls out before changing them.
- If the handoff says "X is broken" or "Y is next," confirm against current state before committing to that framing.

**Drift check — before treating the summary as context.** The summary file's mtime marks when the snapshot was taken. Check whether anything has changed in the working tree since then:

- For git repos: `git status --short` for uncommitted state, plus any commits or tracked files newer than `.CLAUDE_LAST_SESSION.md`.
- For non-git directories: `find . -newer .CLAUDE_LAST_SESSION.md -type f` (excluding obvious build/output dirs).

If anything is newer, surface a brief drift note up front — which files or commits postdate the summary — so its claims about them are flagged as potentially stale. If nothing is newer, stay silent and proceed.

If the file doesn't exist, inform the user (they may be starting fresh) and proceed with their request.

After loading the context, help the user with their request. They may have provided additional instructions after this command, or they may follow up with a question about what to work on next.
