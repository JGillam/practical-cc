---
description: Triage which open GitHub issues are still remaining on the current branch and recommend what to do next.
---

Launch the `remaining-issues` subagent (via the Agent tool, with
`subagent_type: "whats-next:remaining-issues"`) to investigate which open GitHub issues are
genuinely remaining — i.e. open issues whose fix is NOT already present on the current local
branch — and to return a ranked shortlist of what to do next.

Do the analysis in the subagent's own context. When it returns, relay its shortlist to me
verbatim (you may add a one-line note if something looks off, e.g. `gh` wasn't authenticated
or the repo has no GitHub remote).

Do not start implementing any issue unless I ask.

$ARGUMENTS
