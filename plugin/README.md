# claw-retro plugin

An instructions-only Claude Code plugin with one skill, `claw-retro`: an
end-of-session retrospective (Keep / Drop / Try applied to an agent session).

## What the skill does

1. Reconciles the session with notes and decisions made since (aligned / drift / to propagate).
2. Builds a deterministic inventory from `git log` and recently changed files, not from memory.
3. Logs this session's failures to a breakage journal; a prevention mechanism only on the third dated case.
4. Summarizes the arc in 3 to 7 beats, including what did not work.
5. Classifies every artifact as keep, one-off or promote, with a tested check and a consumer check.
6. Routes each durable rule to exactly one home and names its "door" (the skill step, hook or scheduled check that runs it).
7. Archives the retro as an append-only note and prints a filled `/compact` paste-block in the chat.

## Install and use

```text
/plugin marketplace add tonydzi/claw-retro
/plugin install claw-retro@claw-retro
```

At the end of a work session, type `/claw-retro` or ask the agent to wrap up the session.

## Side effects

The skill writes a new retro note (for example `retros/retro-<date>-<topic>.md`) and may
add lines to your rules file or a `BREAKAGE.md` journal. Tell the agent where your rules
file and notes folder live; nothing is hardcoded.

## Contents

Markdown instructions, JSON metadata and an icon only. No scripts, no server, no network calls.
