# Plan first — one plan chat, then one step per chat

> The 1st chat is **plan only**: all research, the selection, and the plan docs
> — like CodeC's `docs/` system, scaled to a small app. Nothing is created in
> it. Execution starts only after the plan gate, and it runs **one roadmap row
> per chat**. Question rule everywhere: **ask less, gate always** (§3).

## 1. The two-stage law

| Stage | Chats | Creates | Ends with |
|---|---|---|---|
| **1 · PLAN** | exactly one (P0) | research + the plan docs as chat deliverables | one exit Summary gate (§4), then stop |
| **2 · EXECUTE** | one per roadmap row | the app repo (row 0), then app code row by row | CI green + docs updated + report; merge gate in [RULES](RULES.md) |

- No repository, no app code, no Play/account action in the plan chat.
- Rows run in order. A new row starts only when the previous row is recorded
  done (or explicitly held by the owner).

## 2. The app docs system

Four files, drafted in the plan chat, committed to the app repo **before any
app code**, kept forever. Skeletons live in `templates/docs-system/` and are
frozen into the repo at bootstrap. Modeled on CodeC's `docs/` (research ·
roadmap · journal · phase records), scaled down:

| File | Holds |
|---|---|
| `docs/RESEARCH.md` | 3–5 evidence-backed options (links + check dates), the niche verdict line, **rejected options with reasons**, the pre-written kill test |
| `docs/ROADMAP.md` | numbered rows in execution order; one row = one chat; status 📋 planned · 🚧 in progress · ✅ done · ❌ cancelled (keep the row) |
| `docs/DECISIONS.md` | the dated decision log — **the anti-re-ask register**: owner decisions, law waivers, agent decisions |
| `docs/steps/NN-<slug>.md` | one record per executed row: evidence (`file:line`), what shipped, tests, follow-ups |

Borrowed from CodeC's culture, kept light:

- Evidence before hypothesis: claims carry `file:line` reads or named sources
  with check dates.
- Rejected options stay recorded so later chats never re-litigate them.
- Cancelled rows stay visible (❌), never deleted.
- Facts (version codes, checksums, CI runs, merge shas) are read from the
  repository by the **next** change — never guessed in the change that causes
  them.
- Docs ride with the code commit they describe.

## 3. Question policy — ask less, gate always

Three classes. When in doubt: decide reversibly and record, don't ask.

### GATE — always ask; never act without an explicit yes

Permanent, external, money, or owner-reserved (this list also restates
[RULES](RULES.md) "GitHub authority and approval gate"):

- create the app repository (and its visibility + license)
- app name + package ID — **permanent once published**
- git author identity designated for the new repo
- license choice (MIT or GPL-3.0) if not already fixed
- open a PR · merge · push to `main` · release · publish · deploy · submit to
  Play · tag · dispatch an expensive/destructive workflow
- money in any form (ad accounts, paid SDKs or services, any spending)
- legal, tax, store-account actions, and anything with tester personal data
- waiving or rewriting a RULES.md law (e.g. the four-week budget — law 3)
- changing any answer already recorded in `DECISIONS.md`

**How to ask:** one Summary batch at the gate moment, ≤ 4 questions, each
naming its gate ("the gate START.md stage 1 puts in front of any repo"). Never
a second batch for the same gate.

### DECIDE-ONCE — ask during the plan chat only, then record

Product-shaping choices the plan cannot honestly assume: target languages/
locales, monetization model, scope cuts, time budget, design direction.

- Ask them in **one** batch (≤ 4) at the point the plan needs the answer.
- Record every answer in `docs/DECISIONS.md` with its date **the moment it is
  given** (in chat, before the files exist — then paste into the file).
- Later chats read `DECISIONS.md` before asking anything.
  **Re-asking a recorded answer is a defect, not caution.** Changing one is a
  GATE.

### DEFAULT — never ask

- Facts you can research — research, cite source + check date; name the gap if
  evidence is thin instead of asking the owner to fill it.
- Reversible implementation choices — decide, log under "Agent decisions" in
  `DECISIONS.md`, marked reversible on objection.
- Anything already answered in this chat or these docs — record it, use it.
- Taste with an obvious default — take the default, note it.

### Hygiene (all stages)

- Before any question: read `ROADMAP.md` + `DECISIONS.md` (or the plan in
  chat). If the answer is there, use it silently.
- If an answer would not change the plan or the code, it is not a question.
- The owner may say "decide X yourself" — that becomes an agent-decision entry.
- At most one question batch per gate moment per chat.

## 4. The plan chat's exit gate (one Summary, then stop)

1. Plan: approve / revise / hold?
2. Authorize creating the app repository? (public/private · MIT/GPL-3.0)
3. Which git author identity is designated for the new repo?
4. Working name + package ID? (package ID is permanent once published; the
   official Play title goes to AppFlow's `APP_LIST.md` only when confirmed)

The DECIDE-ONCE batch is asked earlier in the same chat — not at this gate.
Then stop. No repo, no code until the owner answers this gate.

## 5. Execution chats (one row per chat)

First message of every execution chat:

```text
Read the public playbook repo https://github.com/pabi277/AppFlow at commit <SHA>
and follow START.md stage 2. Implement roadmap step <N> only for <APP>.
Read docs/ROADMAP.md and docs/DECISIONS.md first; never re-ask a recorded
decision; GATE items only per PLAN.md §3.
```

Each chat ends: the row's status updated in `ROADMAP.md`, its
`docs/steps/NN-<slug>.md` record written, CI green, a short report, and a stop
at the merge gate.
