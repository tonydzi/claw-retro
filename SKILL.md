---
name: retro
description: >-
  End-of-session retrospective: recall & reconcile against everything decided since, inventory
  what was actually built (git + touched files, not memory), classify each artifact
  keep/one-off/promote, route durable rules to exactly one permanent home with a "door" audit,
  archive the retro as a note in the 7-header compact format, and PRINT the ready /compact
  paste-block inline. Trigger on "/retro" or any end-of-session wrap-up request.
---

# /retro — session retrospective (what we built · what we keep)

A retro is the Agile end-of-cycle ritual (Keep / Drop / Try) applied to an agent session:
look back, decide what survives. Goal: **nothing reusable drowns in the transcript.**

## Step 0 — Recall & reconcile FIRST

Before any inventory, situate this session against the whole collaboration — it may be running
hours or days after the work, and parallel sessions may have already captured or superseded
things:

- Check recent retros / notes on the same topic (your notes folder, your rules file's git log).
- Check what changed SINCE this session's work happened (`git log --since`).
- For every rule or decision this session touched: already captured elsewhere? superseded?

Output one tight block: **✅ aligned** / **⚠️ drift** (session did X but Y was decided elsewhere
— flag it) / **🔗 to propagate** (durable work not yet routed). If a parallel session already
captured an item, cross-link instead of re-capturing.

## Step 1 — Deterministic inventory

Ground the recap in facts, not the agent's memory of itself:

```bash
git log --oneline --since="1 day ago" --stat
```

plus recently-modified files in your skills/scripts/notes directories. Cross-check against what
was created in THIS conversation: files, rules, decisions, flagged items. Anything in the diff
that this session did NOT create belongs to someone else — flag, never claim.

## Step 1b — Breakage journal

List this session's failures (own mistakes, tool failures, silent wrong outputs caught late).
One line each into a persistent `BREAKAGE.md`: what · conditions · suspected cause (mark
🤔 hypothesis vs ✅ proven). Count occurrences of the same class across the journal — build a
prevention mechanism only on the **third** dated occurrence, not the first (premature mechanisms
are how you end up with 60 watchdogs nobody reads). Exceptions that get fixed immediately: data
loss, security, broken safety gates.

## Step 2 — Summarize the arc

3–7 beats: starting intent → what got built → key realizations → what was decided. Honest and
concise — including what did NOT work.

## Step 3 — Classify every artifact

For each thing made this session, audit **tested? ✅/❌** (did it get a real test when built —
if not, flag it), then classify:

- 🟢 **Keep & reuse** — permanent infra or a tool you'll run again.
- 🟡 **One-off** — served its purpose; if the *pattern* matters, capture the pattern, let the
  artifact rest.
- ⬆️ **Promote** — ad-hoc today, should become a rule / skill / scheduled check.

Also run the **consumer check** on every 🟢/⬆️ item: built → handed over → actually USED?
"Built" without a named consumer is not done — either connect a consumer or admit it's shelfware.

## Step 4 — Route durable items, each to exactly ONE home

- Reusable tool/script → note its path + when to re-run in your memory/notes layer.
- Behavioral rule for the agent → rules file (CLAUDE.md / AGENTS.md) — short trigger + gist +
  pointer, details live one level down.
- Recurring ritual → its own skill file.
- "Every time X happens automatically" → a hook, not prose.
- Time-based recurrence → a scheduled task.
- **Never duplicate a rule across homes** — one canonical home, others point to it.

**Door audit (the step most setups miss):** for EVERY rule captured, name the executable path
that will invoke it — a skill step, a hook, a scheduled check. Our measured baseline before this
audit existed: 19 of 25 fresh rules had no door; one rule sat 42 days without firing once.
No door → add one now (a line in an existing skill beats a new robot), or explicitly log the
rule as unverifiable **with the named cost of its silent death**.

## Step 5 — Archive the retro as a note

Write one note (e.g. `retros/retro-YYYY-MM-DD-topic.md`): frontmatter + the arc + the
classification table + **the 7-header distillation** (DECISIONS / TODO / NOW / PATHS & VALUES /
COUNTERS / OPEN / TOOLS & CONTRACTS — format: [compact-canon](https://github.com/tonydzi/compact-canon)).
The note doubles as the compact summary, so retro and compact are never written twice.
Append-only: never overwrite an existing retro.

## Step 6 — PRINT the ready compact block inline (mandatory output)

Fill the 7-header skeleton from compact-canon's `COMPACT.md` with THIS session's real facts
(reuse the Step-5 distillation — don't re-derive), and print **one fenced code block starting
with `/compact `**, preceded by: "➤ Copy the whole block and paste it as your next message."

- ⛔ **A pointer is not a block.** "Take the block from such-and-such file" is a violation —
  the filled block must be printed in the chat, ready to copy. (We shipped the pointer version
  first; the human vetoed it. Learn from our bruise.)
- ⛔ An empty skeleton with `<...>` placeholders is also a violation.
- The agent cannot press `/compact` itself — printing the ready line is the agent's half,
  pasting is the human's.

Close with the fork: *"Everything is archived. Staying in this session → paste the block below.
Starting fresh → just leave, nothing depends on the paste."*

## Scope

Internal build-retro only — not a public changelog, not a standup report. If the session built
nothing durable, say so plainly and skip the ceremony (but still offer the compact block if the
chat got long).
