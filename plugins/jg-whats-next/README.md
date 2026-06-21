# What's Next Plugin (jg-whats-next)

A `/whats-next` slash command that tells you which open GitHub issues are *actually* still
remaining on your current branch — and what to tackle next.

## Overview

In many repos, "open issue" drifts away from "unfinished work": GitHub only auto-closes an
issue when a merged commit/PR uses a closing keyword (`Fixes #N`), and plenty of teams don't.
So issues pile up `open` long after they shipped. A naive `gh issue list` overcounts the work
that's left.

This plugin does the careful version. `/whats-next` hands the analysis to a read-only subagent
that cross-references **commit history against actual repo content** to classify each open
issue as done-but-stale, partially done, or genuinely remaining — then returns a ranked, short
list of what to do next, with file/commit evidence for anything it calls "done."

It only reports. It does not edit files, commit, or push.

## Command

### /whats-next

Triages open issues on the current branch and returns:

- **Recommended next (shortlist)** — top 3–5 remaining/partial issues by value-vs-effort, with
  rough effort sizing and any dependencies called out.
- **All remaining / partial** — each open issue still needing work, with a one-line status.
- **Likely done but still open** — stale-open issues that are candidates to just close, with
  the commit or file that satisfies them.

The command delegates to the bundled `remaining-issues` subagent (invoked as
`whats-next:remaining-issues`), so the issue-by-issue investigation runs in its own context and
only the shortlist comes back to your main session.

## Requirements

- **[GitHub CLI](https://cli.github.com/) (`gh`) installed and authenticated** (`gh auth status`).
- The repo has a **GitHub remote and uses GitHub Issues.** The agent fails loudly (rather than
  guessing) if `gh` is missing/unauthenticated or the repo isn't on GitHub. Non-GitHub issue
  trackers (GitLab, Jira, etc.) are not supported.

## Installation

This plugin is installed by registering the practical-cc marketplace in Claude Code. Once
registered, the `/whats-next` command becomes available automatically.

For detailed installation instructions, see the
[Claude Code Plugin Documentation](https://code.claude.com/docs/en/plugins).
