---
description: Start-of-session context loader — reads the previous session's handoff from .CLAUDE_LAST_SESSION.md.
disable-model-invocation: true
---

Read the session summary from .CLAUDE_LAST_SESSION.md and use it as context for this session.

If the file doesn't exist, inform the user (they may be starting fresh) and proceed with their request.

After loading the context, help the user with their request. They may have provided additional instructions after this command, or they may follow up with a question about what to work on next.
