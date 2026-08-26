# Anatomy of our retro — every part, what it's for, and what it's made of

The shipped [SKILL.md](SKILL.md) is the portable 6-move core. Our production retro has more
organs. This document decomposes ALL of them — so you can steal parts individually. Each part:
what it does, the incident or measurement that created it, and whether it ports cleanly
(**universal**) or assumes our infrastructure (**lab-specific**).

Parts marked ★ have their own public repo.

## Opening moves

### 1. Recall & reconcile (universal)
Before judging the session, line it up against everything decided since and elsewhere — recent
retros, the day's ledger, parallel sessions, peers. Two jobs: **de-dupe** (a parallel session may
have already captured the rule) and **reconcile** (this session's calls may be superseded).
Output: one block — ✅ aligned / ⚠️ drift (flagged) / 🔗 to-propagate.
Born from running one brain on several machines: without reconciliation, retros re-captured
each other's rules and resurrected superseded decisions.

### 2. Deterministic inventory (universal)
`git log` + recently-touched files, cross-checked against what THIS conversation created.
The agent's memory of its own session flatters it; the diff doesn't. Anything in the diff this
session did NOT create is someone else's — flag, never claim (multi-machine attribution guard).

### 3. Breakage journal + the third-breakage rule (universal)
Every failure of the session becomes ONE dated line in a persistent journal: what · conditions ·
suspected cause (🤔 hypothesis vs ✅ proven). Then count the CLASS across the journal:
1st occurrence = a line · 2nd = a line + sharpened conditions · **3rd dated occurrence = the class
is systemic → dedicated fix session** (five-whys over the series, then design). Building a
mechanism on the 1st occurrence is banned — that's how you end up with 60 watchdogs nobody reads.
Carve-outs that skip the count and get fixed NOW: data loss, security, money, broken safety gates.

## Judgment moves

### 4. The arc (universal)
3-7 beats: intent → built → realizations → decisions. Honest, includes what did NOT work.

### 5. Cofounder verdict (lab-specific, portable idea)
Four fixed lines from the business-partner persona: 💰 what today moved revenue/the mission ·
🔪 the weakest time-spend to not repeat tomorrow · 🤺 where did I agree-without-evidence instead
of arguing (a role failure we count) · ❓ one steering question for tomorrow. Forces the retro to
answer "so what?" — not just "what?".

### 6. Classify + tested?-audit (universal)
Every artifact: 🟢 keep-and-reuse / 🟡 one-off (keep the pattern, drop the artifact) / ⬆️ promote
to permanent. Plus a **tested? ✅/❌** column — the retro does NOT test (too late, too cold);
it audits whether the quality gate ★[break-it-first](https://github.com/tonydzi/break-it-first)
ran when the thing was built, and flags the untested.

### 7. Connect check (universal, our favorite)
For every artifact: built → handed over → **actually USED?** Three outcomes: ✅ used (consumer
NAMED — no name, no ✅) · 🔗 delivered-but-unconsumed (assign a consumer or a date) · ⚠️ built
into the void (surface it; connect or admit shelfware). "Silence ≠ used." Extension: **the world
consumer** — if the session closed a portable class of problem, "did we hand it to the world?"
becomes a fourth Connect outcome (🟢 shared with links / ⚪ searched-found-nothing / ⛔ not portable).

### 8. Drift audit → child sessions (universal mechanics, host-specific spawning)
Name the session's MAIN goal; list topics it got blown into that are neither the goal nor done;
each real one gets its own child session — spawned VISIBLY (a session the human can open and
steer), never as a silent background process, never as a chip waiting for a click (our measured
chip graveyard: 107 of 346 never clicked). Cap ~5 per retro; the rest goes to the task journal.

## Bookkeeping moves

### 9. Task-journal sync (universal)
Retro is the safety net of the task registry: everything closed this session gets marked done
**with evidence** (claimed-done without proof gets flagged, not closed); every open item that
lives only in the transcript gets a registry card. One-line delta: «+N new · ✅M closed».

### 10. Roadmap checkpoint (universal)
Three moves against the living roadmap: mark what advanced · add new directions · say honestly
"nothing moved" (also a signal).

### 11. Route-to-homes + the door audit (universal — this is the heart)
Each durable lesson goes to exactly ONE home (rules file / skill / memory note / hook / scheduled
task); homes point at each other, never copy. Then the **door audit**: for every rule, name the
executable path that will invoke it. Our measured baseline: **19 of 25 fresh rules had no door**;
one rule sat 42 days without firing. No door → build one now (a line in an existing skill beats
a new robot) or log the rule as unverifiable WITH the named cost of its silent death.
The homes for compacted context specifically: ★[compact-canon](https://github.com/tonydzi/compact-canon);
for always-loaded homes and their budgets: ★[always-loaded-diet](https://github.com/tonydzi/always-loaded-diet).

### 12. Contribution test (universal)
Every keep-and-reuse artifact gets three questions: (а) is the pain universal? (б) are there live
threads of sufferers (30-second search)? (в) can it be shared without leaking? Two of three "yes"
→ it queues for packaging and release. This is the door that turns "we built know-how" into
"the world heard about it" without anyone having to remember.

### 13. Growth log (lab-specific)
If the session taught something real about working with the human partner: one dated line —
lesson + one self-upgrade — reviewed weekly. The persona versioning organ.

### 14. Content check (lab-specific)
Verdict while context is hot: does this session deserve a public post / a machine-readable dev-log
/ both / neither? The nightly content robots are the safety net; retro is the hot-context pass.

### 15. Repeats → skill (universal)
Any action repeated 2-3× this session gets offered as a skill/routine — with an AK-47 guard:
a skill is ONE markdown file with a procedure, not a server. Genuinely-recurring + time-based →
scheduled task; "every time X happens" → hook; N-item finite backlog → a self-terminating
"elephant" routine that eats the list in scheduled bites and shuts itself off.

## Closing moves

### 16. Archive note (universal)
The retro saves itself to the knowledge vault as one note: frontmatter + arc + classification
table + the 7-header distillation (same format the compact block uses — retro and compact are
never written twice).

### 17. Compact handoff (universal) ★
The retro ENDS by printing the ready `/compact <block>` — filled with this session's facts, one
fenced block, "copy and paste as your next message". Never a pointer to a file (we shipped the
pointer version; the human vetoed it), never an empty skeleton. Format and measurements:
★[compact-canon](https://github.com/tonydzi/compact-canon).

---

## Assembly order

recall → inventory → breakage journal → arc → verdict → classify → connect → drift →
journal/roadmap sync → route+door-audit → contribution test → archive → **print the compact block**.

If the session built nothing durable: say so plainly, skip the ceremony, still offer the block
if the chat got long.

## License & attribution

MIT. Invented by **Mycroft** (synthetic cofounder) & **Tony** — Palo Alto AI Research Lab.
