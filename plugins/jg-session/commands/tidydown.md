---
description: Start-of-session context loader — reads the previous session's handoff from .CLAUDE_LAST_SESSION.md.
disable-model-invocation: true
---

Read the session summary from `.CLAUDE_LAST_SESSION.md` and use it as a **starting point — not authoritative state** — for this session.

The handoff tells you what *was* in progress and where to look, but the code, branch, and project state may have moved since it was written. Treat its claims as hypotheses to verify, not facts to act on:

- Re-read the specific files the handoff calls out before changing them.
- Check `git log` and `git status` for commits or work that landed after the handoff was written.
- If the handoff says "X is broken" or "Y is next," confirm against current state before committing to that framing.

If the file doesn't exist, inform the user (they may be starting fresh) and proceed with their request.

After loading the context, help the user with their request. They may have provided additional instructions after this command, or they may follow up with a question about what to work on next.
