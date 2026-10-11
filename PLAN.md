# Plan first — one plan chat, then one phase per chat

> The 1st chat is **plan only**: all research, the selection, and the plan docs
> — like CodeC's `docs/` system, scaled to a small app. Nothing is created in
> it. Execution starts only after the plan gate, and it runs **one phase per
> chat** — a phase is a decent chunk of work (2–4 parts), not a sliver, so v1
> finishes in a handful of chats. **Every phase ends with a downloadable APK**
> so progress is visible. Question rule everywhere: **ask less, gate always**
> (§3). AppFlow is frozen reference; the app lives by its own `prompt.md` (§6).

## 1. The two-stage law

| Stage | Chats | Creates | Ends with |
|---|---|---|---|
| **1 · PLAN** | exactly one (P0) | research + the plan docs as chat deliverables | one exit Summary gate (§4), then stop |
| **2 · EXECUTE** | one per phase | the app repo (phase 0), then one working increment per chat | CI green + **downloadable APK artifact** + docs updated + report; merge gate in [RULES](RULES.md) |

- No repository, no app code, no Play/account action in the plan chat.
- Phases run in order. A new phase starts only when the previous phase is
  recorded done (or explicitly held by the owner).

## 2. The app docs system — the self-contained set

These files, drafted in the plan chat and committed to the app repo **before
any app code**, make the repo workable **without any other repo**. Skeletons
live in `templates/` (`docs-system/`, `rule-app.md`, `prompt-app.md`,
`readme-app.md`) and are frozen into the repo at bootstrap:

| File | Holds |
|---|---|
| `README.md` | what the app is (from `templates/readme-app.md`, provenance line kept) |
| `rule.md` (repo root) | **the app's own operating manual** — laws, merge gate, question policy, work cycle, invariants, definition of done. Self-contained: authoritative even if AppFlow is unreachable (`templates/rule-app.md`) |
| `prompt.md` (repo root) | the **self-contained continuation prompt** — paste it into the next chat; updated at every phase end (§6, `templates/prompt-app.md`) |
| `docs/RESEARCH.md` | 3–5 evidence-backed options (links + check dates), the niche verdict line, **rejected options with reasons**, the pre-written kill test |
| `docs/ROADMAP.md` | numbered **phases** in execution order; one phase = one chat; status 📋 planned · 🚧 in progress · ✅ done · ❌ cancelled (keep the row) |
| `docs/DECISIONS.md` | the dated decision log — **the anti-re-ask register**: owner decisions, law waivers, agent decisions |
| `docs/phases/NN-<slug>.md` | one record per phase: its parts, evidence (`file:line`), what shipped, tests, **what the APK shows** |

That is the whole set — nothing else is needed from anywhere.

### Phase sizing (decent chunks, not slivers)

- A phase is **one whole capability** of the app (e.g. "editor with file CRUD",
  "terminal UX", "ads + ad-free purchase"), split into **2–4 parts** listed in
  its phase record. Each part is verifiable; the phase lands as one increment.
- A v1 roadmap is roughly **5–8 phases** including bootstrap. If a roadmap
  grows past ~10 phases, the phases are too small — merge them.
- Anything smaller than about half a day of work joins a neighboring phase.
  Split a phase only when it genuinely cannot land in one chat, and record why.
- Bugs reported later are their own small fix chats — they don't need phases.

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

## 5. Phase chats (one phase per chat, APK every time)

First message of every phase chat is the app's own **`prompt.md`**, pasted as
it stands (§6) — it already carries the rules digest and the state — followed
by the owner's command, e.g. `start phase 3`.

Each phase chat ends with **all** of:

1. every part of the phase implemented; its "Done means" cell in `ROADMAP.md`
   is the acceptance test, and no feature outside this phase may be added;
2. CI green, and the run's **`app-progress-apk` artifact downloadable** — the
   owner can sideload it and see this phase's increment (it is progress, not a
   release);
3. `docs/phases/NN-<slug>.md` written (including a line on **what the APK
   shows**), the roadmap row's status updated;
4. `prompt.md` updated in the same commit (state, CI run, APK note, next
   phase);
5. a short report (run id, tip sha, APK artifact name, what is now visible),
   and a stop at the merge gate.

## 6. Frozen playbook, self-contained app

- **The app repo depends on nothing.** Its `rule.md` holds the full laws
  (branching, merge gate, question policy, work cycle, invariants), its
  `prompt.md` the living state and continuation instruction, its `docs/` the
  plan and decisions. A later chat works from this repo alone.
- **AppFlow is frozen reference and provenance.** An app pins one full SHA at
  bootstrap; its copied `templates/` + `knowledge/` snapshot is never edited
  in the app repo. App work never waits on an AppFlow change — AppFlow itself
  changes only by deliberate owner review ([MAINTENANCE](MAINTENANCE.md)).
- The owner pastes `prompt.md` into the next chat and says `start phase N`
  — or reports a bug. The pinned playbook SHA stays in the provenance line
  and `rule.md` header for history, not for reading.
