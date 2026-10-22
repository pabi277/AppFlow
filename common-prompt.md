# common-prompt.md — start a new app (used ONCE per app)

Paste the block below as the **first message of a brand-new chat** — one
fresh chat per app, once. It launches the plan-only first chat
([PLAN.md](PLAN.md) stage 1): all research, the selection, and the complete
self-contained plan file set — then it stops at the exit gate. No repository
and no code exist at this point.

Before pasting:

1. Replace `<SHA>` with this playbook's pinned full commit SHA (40 chars).
2. Fill `[MY CONTEXT]` with your interests, experience, target users,
   languages, time, and anything already decided. Better context = better
   research = fewer questions.
3. Replace `[AREA, IF ANY]` with a domain (e.g. "mess bills, hostels,
   students") — or delete that sentence to let research roam free.

After the exit gate is answered, the app gets its own repo with `rule.md`,
`prompt.md`, and `docs/` — and **never needs this file again**. Every later
chat starts from that repo's own `prompt.md`.

```text
Plan-only session — creates NO repository, branch, commit, or app code.
Everything happens in chat and as plan files in this workspace. Never paste
secrets, account IDs, tester contacts, or real ad IDs.

Before anything else, read the public playbook
https://github.com/pabi277/AppFlow at commit <SHA> — PLAN.md, START.md,
RULES.md, PROMPTS.md (P0), templates/rule-app.md, templates/prompt-app.md,
and knowledge/niche-method.md — and follow PLAN.md stage 1 exactly. That
commit is the pinned playbook for this app.

Goal of this ONE chat: all research and a complete, self-contained plan for a
new Android app — then stop at the exit gate.

MY CONTEXT (already filled above): [MY CONTEXT]. Preferred area, if any:
[AREA, IF ANY].

1. Research 3–5 differentiated Android app opportunities for Indian users
using current Play Store evidence and knowledge/niche-method.md. For every
option report: the target user and their painful job, the exact search phrase,
country/date, linked Play listings, market crowding, and any verified review
signals. Deep-dive the leading one or two: their top five relevant listings
and ten recent one-star reviews each. Separate observed facts from inference
and state uncertainty. Include my real advantage, a distinct offline-first
v1, privacy/licensing/policy risks, plausible monetization (no revenue
promises), and a measurable kill test written before results.

2. Question policy — ask less, gate always (PLAN.md §3): record every answer
with its date the moment it is given (it belongs in docs/DECISIONS.md) and
NEVER re-ask a recorded answer — that is a defect, not caution. Researchable
facts are researched and cited, not asked. Reversible choices are your
agent-decisions, logged as reversible on objection. Exactly TWO question
batches exist in this whole chat:
   (A) with the comparison table: my direction pick (combine/refine allowed)
       plus at most 4 DECIDE-ONCE items (languages/locales, monetization
       model, scope cuts, time budget — a budget beyond four weeks is a
       RULES.md law-3 waiver and is recorded as such);
   (B) the exit gate in step 5.
If an answer would not change the plan or the code, it is not a question.

3. Present the comparison table and recommend the strongest one or two — do
not choose for me.

4. After my pick, write the COMPLETE self-contained file set as copyable
markdown (PLAN.md §2) — the future app repo must work with no other repo
reachable:
   - docs/RESEARCH.md — options + evidence with check dates, rejected options
     with reasons, the niche verdict line, the pre-written kill test, and the
     REUSE MAP (knowledge/reuse-first.md §2 scan, whole app: architecture
     base, ONE UI base sample, data/offline, ads/billing — per capability a
     verified candidate with licence + activity checked today, and a
     DEPEND / ADAPT / STUDY / BUILD / REJECT verdict; rejected candidates
     stay listed with reasons). Price the roadmap on reuse, not on writing
     everything from scratch;
   - docs/ROADMAP.md — numbered PHASES (2–4 parts each; v1 ≈ 5–8 phases;
     phase 0 = bootstrap; merge anything smaller than half a day of work into
     a neighbour), every "Done means" cell including the downloadable APK
     that shows the phase's increment;
   - docs/DECISIONS.md — every answer so far, dated; law waivers in their own
     section;
   - rule.md — from templates/rule-app.md, filled with identity, time budget,
     and any waivers;
   - prompt.md — from templates/prompt-app.md, filled with identity and the
     next phase;
   - README.md — from templates/readme-app.md, filled.
Sketch screens and the asset/data schema inside phase records — never as code.

5. Exit gate — ONE Summary batch and nothing else, then STOP (no repo, no
code until I answer): plan approve / revise / hold? · authorize creating the
app repository (public or private · MIT or GPL-3.0)? · which git author
identity is designated for the new repo? · working name + package ID
(package ID is permanent once published)?
```
