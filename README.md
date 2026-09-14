# claw-retro

**An end-of-session retrospective ritual for coding agents that turns a finished session into durable rules, a permanent archive note, and a ready-to-paste compact block — so nothing the agent learned dies with the transcript** — the six moves ship as [SKILL.md](SKILL.md).

## The pain, in your words

- *"I keep re-teaching my agent the same conventions every week."*
- *"We made a decision last Tuesday and today the agent cheerfully contradicted it."*
- *"The lesson is in there somewhere — in a 200k-token transcript I will never reread."*
- *"My CLAUDE.md grows, but half the rules in it never fire."*

Memory-bank systems (Cline-style living files) and handoff snapshots solve adjacent problems. This one is different: **the moment a session ends is the only moment its lessons are cheap to extract** — context is hot, evidence is one scroll away, and [ANATOMY.md](ANATOMY.md) takes the ritual apart move by move. An hour later it's archaeology.

## Numbers (from our own fleet audits — internal, dated, honest)

| Audit | Result |
|---|---|
| Freshly captured rules that had NO invocation path ("door") until a retro audit forced one (2026-08-06) | **19 / 25 (76%)** |
| Longest a written-and-blessed rule sat in our canon without firing once | **42 days** |
| Stock compactions that preserved our custom format without the retro's paste-block bridge | **0 / 354** ([measured](https://github.com/tonydzi/compact-canon/blob/main/MEASUREMENTS.md)) |

The first two numbers in [ANATOMY.md](ANATOMY.md) are the reason retro exists at all: **writing a rule down is not the same as the rule working.** A rule with no executable path that invokes it dies silently.

## Self-diagnosis in 30 seconds

```bash
git log --oneline -15 -- CLAUDE.md AGENTS.md .cursorrules
```

You work with your agent daily. If the last time a *durable rule* was written back is weeks ago — your lessons are dying in transcripts. That's the disease this ritual treats.

## The ritual (6 moves, run at session close)

1. **Recall & reconcile.** Before judging this session, [SKILL.md](SKILL.md) lines it up against everything decided since and elsewhere (other sessions, other machines, the docs). Catches drift, superseded decisions, and duplicates *before* they get re-captured.
2. **Deterministic inventory.** `git log` + recently-touched files — [SKILL.md](SKILL.md) grounds the recap in facts, not in the agent's memory of itself.
3. **Classify every artifact:** 🟢 keep-and-reuse · 🟡 one-off (capture the *pattern*, discard the artifact) · ⬆️ promote to permanent.
4. **Route each durable item to exactly ONE home** (rules file / skill / memory / hook / scheduled task) — homes *reference* each other, never copy, because copies drift; the routing table is in [ANATOMY.md](ANATOMY.md). Then the **door audit** in [SKILL.md](SKILL.md): for every captured rule, name the executable path that will invoke it. No door → build one now (a line in an existing skill is cheaper than a new robot) or explicitly log the rule as unverifiable with the cost of its silent death.
5. **Archive the retro as a note** — in the same 7-header format the compact block uses, so retro and compact are never written twice.
6. **Print the ready `/compact <block>` inline** — filled with this session's facts, one fenced block, "copy and paste as your next message". **Never a pointer to a file.** We shipped the pointer version first; the human vetoed it within weeks ("go take the text from that file yourself" is not a deliverable). The block format and why inline-paste is the only path that works: [compact-canon](https://github.com/tonydzi/compact-canon).

A drop-in, de-personalized skill implementing the ritual for Claude Code: [SKILL.md](SKILL.md) → copy to `~/.claude/skills/retro/SKILL.md`, trigger with `/retro`.

Want the FULL production version, organ by organ? [ANATOMY.md](ANATOMY.md) decomposes all 17 parts of our real retro — breakage journal, door audit, connect check, drift-spawned child sessions — each marked universal vs lab-specific, so you can steal parts individually.

## Design choices

- **A skill is one markdown file**, [SKILL.md](SKILL.md): no server, no DB, no webhook. If your retro needs infrastructure, it will not survive a busy week.
- **Retro is the safety net, not the only net.** Capture rules in-flight when you can; retro catches what slipped. Both write to the same homes.
- **Evidence over vibes.** "Closed" requires proof (a passing test, a commit, a counter). Claimed-done without evidence gets flagged, not celebrated.
- **Agent-agnostic idea, Claude-Code-native reference.** The shipped SKILL.md targets Claude Code; the six moves port to any agent that can read its own git log.

## FAQ

**How is this different from a memory bank (Cline-style)?** Complementary. Memory banks are living files the agent maintains *during* work; retro is a *closing* distillation that decides what deserves permanence and routes it. Banks answer "where am I?"; retro answers "what survives me?".

**How is this different from handoff tools?** A handoff is a snapshot for the *next* session. Retro produces durable rules (forever), an archive note (forever), and a compact block (for *this* session's continuation). Different lifetimes.

**Why route to ONE home?** Because two copies of a rule diverge, and the stale one wins at the worst moment. One canonical home + pointers.

**What exactly is a "door"?** An executable path that invokes the rule: a skill step, a hook, a scheduled check. Our own audit in 2026 found 76% of fresh rules had none — they were prose nobody would ever run. A rule without a door is a wish.

**Does the agent run this itself?** Yes — that's the point. You type `/retro`; the agent does the six moves of [SKILL.md](SKILL.md) and hands you the paste-block. The human's only job is pasting one block.

## Attribution & license

Invented by **Mycroft** (synthetic cofounder) & **Tony** — [Palo Alto AI Research Lab](https://github.com/tonydzi). MIT license.

Siblings: [compact-canon](https://github.com/tonydzi/compact-canon) (the measured paste-block format this ritual emits) · [break-it-first](https://github.com/tonydzi/break-it-first) (the quality gate whose verdicts this ritual audits) · [always-loaded-diet](https://github.com/tonydzi/always-loaded-diet) (the homes durable rules get routed to) · [claw-consensus](https://github.com/tonydzi/claw-consensus) (multi-machine agent consensus).

We hand free working seeds of our lab tooling to engineer-testers — WhatsApp **+1 (341) 222-9178**.

---

<!--ecosystem-map:start-->

## 🧩 One piece of a working system

This repository is one piece lifted out of a live operation: one non-technical founder, an AI
cofounder, and a fleet of machines that reach consensus with each other and wake the human only
for money or the irreversible. It was extracted after it survived production, not written as a
demo — and it runs on its own: nothing here phones home to the rest.

**See how the whole thing fits together → [SYSTEM.md](https://github.com/tonydzi/tonydzi/blob/main/SYSTEM.md)**

Its closest neighbours in the **memory** layer: [`always-loaded-diet`](https://github.com/tonydzi/always-loaded-diet) · [`sqlite-graph-memory`](https://github.com/tonydzi/sqlite-graph-memory) · [`second-brain-starter-kit`](https://github.com/tonydzi/second-brain-starter-kit)

<!--ecosystem-map:end-->

## AI contributors

This project is built by a human + AI team, and the git log says so under the rules in [AI-CONTRIBUTORS.md](https://github.com/tonydzi/.github/blob/main/AI-CONTRIBUTORS.md): Claude writes most of the code, Codex and Grok review it, Gemini feeds the research. Each is credited on a commit
**only if its output changed that commit's content** — no decorative credits. Lab-wide
policy, one source for every repo: [AI-CONTRIBUTORS.md](https://github.com/tonydzi/.github/blob/main/AI-CONTRIBUTORS.md).
