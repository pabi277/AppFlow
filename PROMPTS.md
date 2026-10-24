# Copy-paste prompt library

Replace bracketed fields before sending. Each prompt assumes the app repo has
already frozen `templates/` and `knowledge/` from a pinned playbook commit.
Do not paste secrets, account IDs, tester contacts, or real ad IDs into prompts.
Every prompt also assumes the question policy in [PLAN.md](PLAN.md) §3: **ask
less, gate always** — read `docs/DECISIONS.md` before asking anything, GATE
items are asked (one Summary batch), everything else is researched, defaulted,
or recorded once and never re-asked.

## P0 — plan-only first chat (research + plan docs)

```text
Plan-only session (PLAN.md stage 1): do NOT create any repository, branch,
commit, or app code. Follow AppFlow's PLAN.md §2 (docs system), §3 (question
policy) and §4 (exit gate). Do not paste secrets, account IDs, tester
contacts, or real ad IDs.
Question policy — ask less, gate always: record every answer with its date
the moment it is given (it belongs in docs/DECISIONS.md). Never re-ask a
recorded answer. Researchable facts are researched and cited, not asked.
Reversible choices are your agent-decisions, logged as reversible on
objection. Two question batches exist in this whole chat: (A) the combined
direction + DECIDE-ONCE batch, (B) the exit gate. Nothing else is asked.
1. Research 3–5 differentiated Android app opportunities for Indian users
using current Play Store evidence and knowledge/niche-method.md. Key
constraints (my experience, interests, time, target languages/locales) that
would change the shortlist go into batch (A) — not as one-at-a-time pings.
For every option, report the target user and painful job, exact search
phrase, country/date, linked Play listings, market crowding, and any verified
review signals. Deep-dive the leading one or two: inspect their top five
relevant listings and read ten recent one-star reviews per leading option.
Separate observed facts from inference and state uncertainty. Include my real
advantage, a distinct offline-first four-week v1, privacy/licensing/policy
risks, plausible monetization (without revenue promises), and a measurable
kill test written before results.
2. Present a comparison table and recommend the strongest one or two; do not
choose for me. Batch (A), one Summary, ≤4 questions: my pick of direction
(combine/refine allowed) plus the decide-once items (languages/locales,
monetization model, scope cuts, time budget — a budget beyond four weeks is a
RULES.md law-3 waiver and is recorded as such).
3. After my pick, run the reuse scan (knowledge/reuse-first.md §2, catalogue:
knowledge/open-source-references.md) for the whole app and write the plan
deliverables as copyable markdown blocks:
docs/RESEARCH.md (options plus the REUSE MAP — per capability a verified
candidate with licence + activity checked today and a DEPEND/ADAPT/STUDY/
BUILD/REJECT verdict; price the roadmap on reuse),
docs/UI-REFERENCE.md from templates/docs-system/UI_REFERENCE.md (chosen
reference stack — knowledge/web-ui-references.md §7, default A, a
DECIDE-ONCE with the design direction; every screen+state listed; do NOT
build the site in this plan chat — Phase 0 builds it, I approve it in
chat, tokens freeze before any app UI code,
knowledge/ui-reference-site.md), docs/ROADMAP.md
(numbered **phases**, not slivers — one
phase = one chat = one downloadable APK; 2–4 parts per phase; v1 is ~5–8
phases; if a row is smaller than half a day of work, merge it into a
neighbour), docs/DECISIONS.md (every answer so far, dated; law waivers in
their own section), the repo's own self-contained rule.md from
templates/rule-app.md (identity, time budget, any waivers filled in),
templates/readme-app.md filled, and the app's own self-contained prompt.md
from templates/prompt-app.md (identity + rules digest + state + continuation).
The finished app repo must work with no other repo reachable. Sketch screens
and the asset/data schema inside phase records — never as code.
4. Batch (B), the exit Summary and nothing else (PLAN.md §4): plan
approve/revise/hold · authorize repo creation (public/private, MIT/GPL-3.0) ·
git author identity · working name + package ID. Then stop. No repo and no
code until I answer.
```

## P1 — research app options

```text
Change-control: use only the assigned session branch. Never create/switch
to another branch, push to `main`, force-push, or use `git reset --hard`.
Before committing, verify author/committer identities with `git var` and
inspect the resulting commit before pushing. Use only this app repo owner's
designated address as author; no per-commit ask after designation. If none
is available, stop and ask. Keep committer identity owner-approved. Never
use AppFlow's owner-specific addresses or an agent's personal email/account.
Do not copy personal addresses into tracked app docs; author email may be
public in Git metadata.
Do not create/open a PR without the owner's explicit command in chat; PR
creation and merging are separate approvals. Work one task at a time; do
not parallelize tasks or open a second PR while any PR is open. Check the
current git/PR/CI state and do not duplicate an existing run.
Do not merge, release, publish, deploy, or dispatch an expensive/destructive
workflow without explicit authorization for that action. A code request,
branch push, or green CI is not authorization; stop at the approval gate.
The owner does not need to arrive with a chosen app or niche. Research
3–5 differentiated Android app opportunities for Indian users using current
Play Store evidence and `knowledge/niche-method.md`. If key constraints such as
the owner's experience, interests, time, or target language are missing and
would change the shortlist, ask concise questions first; otherwise proceed.

For every option, report the target user and painful job, exact search phrase,
country/date, linked Play listings, market crowding, and any verified review
signals. Deep-dive the leading one or two: inspect their top five relevant
listings and read ten recent one-star reviews per leading option. Separate
observed facts from inference and state uncertainty. Include the owner's real
advantage, a distinct offline-first four-week v1, privacy/licensing/policy risks,
plausible monetization (without revenue promises), and a measurable kill test.

Rank the options in a comparison table and recommend the strongest one or two
with evidence. Do not choose for the owner: invite them to select, combine, or
refine an option, then stop. Do not create an app repository or write app code
until the owner explicitly chooses a researched direction. If evidence is too
thin, say what to inspect next instead of inventing demand.
```

## P2 — repo initialization

```text
Change-control: use only the assigned session branch. Never create/switch
to another branch, push to `main`, force-push, or use `git reset --hard`.
Before committing, verify author/committer identities with `git var` and
inspect the resulting commit before pushing. Use only this app repo owner's
designated address as author; no per-commit ask after designation. If none
is available, stop and ask. Keep committer identity owner-approved. Never
use AppFlow's owner-specific addresses or an agent's personal email/account.
Do not copy personal addresses into tracked app docs; author email may be
public in Git metadata.
Do not create/open a PR without the owner's explicit command in chat; PR
creation and merging are separate approvals. Work one task at a time; do
not parallelize tasks or open a second PR while any PR is open. Check the
current git/PR/CI state and do not duplicate an existing run.
Do not merge, release, publish, deploy, or dispatch an expensive/destructive
workflow without explicit authorization for that action. A code request,
branch push, or green CI is not authorization; stop at the approval gate.
Proceed only after the owner explicitly selects one of the researched app
options. If no option has been selected, stop before creating a repo or code.
Before app code, read https://github.com/pabi277/AppFlow at pinned commit
[PLAYBOOK_SHA] and follow its START.md. Copy templates/ and knowledge/ into
this new repo as frozen files, add the provenance line to README.md, and commit
that snapshot first. Then commit the plan chat's docs/ files (RESEARCH, ROADMAP,
DECISIONS, from templates/docs-system/) as "Plan docs" before any app code.
Then fill templates/readme-app.md as README.md, choose
MIT, create a minimal Gradle/AGP hello-screen skeleton, wire
ci-build.yml using secret names only, add a unit test, and make CI green with
a signed AAB and APK. Do not commit secrets, account identifiers, real
AdMob IDs, or tester personal data. Stop and report the exact checks that
passed or failed; do not merge or publish without my approval.
```

## P3 — v1 skeleton

```text
Change-control: use only the assigned session branch. Never create/switch
to another branch, push to `main`, force-push, or use `git reset --hard`.
Before committing, verify author/committer identities with `git var` and
inspect the resulting commit before pushing. Use only this app repo owner's
designated address as author; no per-commit ask after designation. If none
is available, stop and ask. Keep committer identity owner-approved. Never
use AppFlow's owner-specific addresses or an agent's personal email/account.
Do not copy personal addresses into tracked app docs; author email may be
public in Git metadata.
Do not create/open a PR without the owner's explicit command in chat; PR
creation and merging are separate approvals. Work one task at a time; do
not parallelize tasks or open a second PR while any PR is open. Check the
current git/PR/CI state and do not duplicate an existing run.
Do not merge, release, publish, deploy, or dispatch an expensive/destructive
workflow without explicit authorization for that action. A code request,
branch push, or green CI is not authorization; stop at the approval gate.
Design and then, only after I approve the plan, implement a tiny offline-first
Android v1 for [NICHE]. Reuse first (knowledge/reuse-first.md +
knowledge/app-engineering.md): follow the plan's reuse map — the named
architecture pattern, ONE adapted UI base sample, theme generated from one
seed colour, a @Preview and a screenshot test per screen — and do not
hand-build any capability the reuse scan has not covered. UI design comes
from the approved reference site (knowledge/ui-reference-site.md): in
Phase 0 build the disposable phone-shaped site (docs/UI-REFERENCE.md
stack), get my in-chat approval, freeze tokens, and only then build
Compose screens copied from — and screenshot-compared against — it.
Keep source
data in versioned assets (no backend or
login unless evidence proves necessary). First list the user problem, the
screens and their purpose, the asset/data schema, accessibility states, and
unit tests. Put rewarded-ad eligibility behind a host-testable Policy
interface with no SDK dependency in core logic. Include loading, empty, and
error states; the app's core value must work offline. Keep the scope publishable
within four weeks. Do not add features outside the approved plan.
```

## P4 — ads wiring

```text
Change-control: use only the assigned session branch. Never create/switch
to another branch, push to `main`, force-push, or use `git reset --hard`.
Before committing, verify author/committer identities with `git var` and
inspect the resulting commit before pushing. Use only this app repo owner's
designated address as author; no per-commit ask after designation. If none
is available, stop and ask. Keep committer identity owner-approved. Never
use AppFlow's owner-specific addresses or an agent's personal email/account.
Do not copy personal addresses into tracked app docs; author email may be
public in Git metadata.
Do not create/open a PR without the owner's explicit command in chat; PR
creation and merging are separate approvals. Work one task at a time; do
not parallelize tasks or open a second PR while any PR is open. Check the
current git/PR/CI state and do not duplicate an existing run.
Do not merge, release, publish, deploy, or dispatch an expensive/destructive
workflow without explicit authorization for that action. A code request,
branch push, or green CI is not authorization; stop at the approval gate.
Wire ads only after I approve the placement plan. Read
knowledge/monetization.md and templates/admob-checklist.md. Use official AdMob
test units during development; keep all IDs as placeholders or protected
configuration, never paste live values into public code or chat. Add UMP consent
flow and privacy-options entry point; request ads only when the current consent
state permits it. Add an ad-free IAP entitlement flag and a restore path. Make
rewarded placements opt-in and interstitials limited to natural breaks; never
interrupt a task. Show the exact files changed and the test proving ads are
blocked when Policy says no. Do not click live ads or submit a purchase.
```

## P5 — publish

```text
Change-control: use only the assigned session branch. Never create/switch
to another branch, push to `main`, force-push, or use `git reset --hard`.
Before committing, verify author/committer identities with `git var` and
inspect the resulting commit before pushing. Use only this app repo owner's
designated address as author; no per-commit ask after designation. If none
is available, stop and ask. Keep committer identity owner-approved. Never
use AppFlow's owner-specific addresses or an agent's personal email/account.
Do not copy personal addresses into tracked app docs; author email may be
public in Git metadata.
Do not create/open a PR without the owner's explicit command in chat; PR
creation and merging are separate approvals. Work one task at a time; do
not parallelize tasks or open a second PR while any PR is open. Check the
current git/PR/CI state and do not duplicate an existing run.
Do not merge, release, publish, deploy, or dispatch an expensive/destructive
workflow without explicit authorization for that action. A code request,
branch push, or green CI is not authorization; stop at the approval gate.
Prepare a release without exposing credentials. First verify green CI, signed
AAB output, version code, target API, privacy policy, Data Safety, content
rating, listing, and tester status. Prefer the reviewed manual AAB handoff if
CI publishing is not explicitly approved. If CI publishing is approved, use
ci-publish.yml and the protected service-account secret configured in GitHub;
never commit or print its JSON. Default to the internal/closed test track, not
production. Give me the artifact name, checksum, track, and exact Play Console
steps. Stop before submitting a production release.
```

## P6 — store listing

```text
Change-control: use only the assigned session branch. Never create/switch
to another branch, push to `main`, force-push, or use `git reset --hard`.
Before committing, verify author/committer identities with `git var` and
inspect the resulting commit before pushing. Use only this app repo owner's
designated address as author; no per-commit ask after designation. If none
is available, stop and ask. Keep committer identity owner-approved. Never
use AppFlow's owner-specific addresses or an agent's personal email/account.
Do not copy personal addresses into tracked app docs; author email may be
public in Git metadata.
Do not create/open a PR without the owner's explicit command in chat; PR
creation and merging are separate approvals. Work one task at a time; do
not parallelize tasks or open a second PR while any PR is open. Check the
current git/PR/CI state and do not duplicate an existing run.
Do not merge, release, publish, deploy, or dispatch an expensive/destructive
workflow without explicit authorization for that action. A code request,
branch push, or green CI is not authorization; stop at the approval gate.
Using this approved niche verdict line: [VERDICT], draft a factual Play short
description (within the current character limit), a long description, and a
shot-list for phone screenshots. Do not invent features, official affiliation,
pass rates, testimonials, or outcomes. Use phrases real users search for
without keyword stuffing. Check current Play asset and metadata rules, cite
their sources and check date, and flag every statement the owner must verify.
Do not upload assets or publish the listing.
```

## P7 — review replies

```text
Change-control: use only the assigned session branch. Never create/switch
to another branch, push to `main`, force-push, or use `git reset --hard`.
Before committing, verify author/committer identities with `git var` and
inspect the resulting commit before pushing. Use only this app repo owner's
designated address as author; no per-commit ask after designation. If none
is available, stop and ask. Keep committer identity owner-approved. Never
use AppFlow's owner-specific addresses or an agent's personal email/account.
Do not copy personal addresses into tracked app docs; author email may be
public in Git metadata.
Do not create/open a PR without the owner's explicit command in chat; PR
creation and merging are separate approvals. Work one task at a time; do
not parallelize tasks or open a second PR while any PR is open. Check the
current git/PR/CI state and do not duplicate an existing run.
Do not merge, release, publish, deploy, or dispatch an expensive/destructive
workflow without explicit authorization for that action. A code request,
branch push, or green CI is not authorization; stop at the approval gate.
Draft polite, specific replies to the five latest reviews pasted below. Do
not expose personal data, argue, ask for a positive rating, promise an
unverified fix, or mention private account details. For bug reports, thank the
reviewer and state only a confirmed next step. For praise, be brief. Mark any
reply that needs owner fact-checking. The owner approves and posts every reply;
do not automate posting.
[PASTE FIVE REVIEW TEXTS WITH NAMES/EMAILS REMOVED]
```

## P8 — kill decision

```text
Change-control: use only the assigned session branch. Never create/switch
to another branch, push to `main`, force-push, or use `git reset --hard`.
Before committing, verify author/committer identities with `git var` and
inspect the resulting commit before pushing. Use only this app repo owner's
designated address as author; no per-commit ask after designation. If none
is available, stop and ask. Keep committer identity owner-approved. Never
use AppFlow's owner-specific addresses or an agent's personal email/account.
Do not copy personal addresses into tracked app docs; author email may be
public in Git metadata.
Do not create/open a PR without the owner's explicit command in chat; PR
creation and merging are separate approvals. Work one task at a time; do
not parallelize tasks or open a second PR while any PR is open. Check the
current git/PR/CI state and do not duplicate an existing run.
Do not merge, release, publish, deploy, or dispatch an expensive/destructive
workflow without explicit authorization for that action. A code request,
branch push, or green CI is not authorization; stop at the approval gate.
Compare the first four weeks of [APP] against the pre-written kill criteria
and the anonymized numbers below. Separate observed facts from interpretation;
include install, activation, retention, useful-action, crash, review, and
revenue counts with date ranges and denominators. Account for tiny samples and
store-review lag. Recommend exactly one: ship next app, or iterate once on a
specific verified blocker. Do not invent thresholds after seeing the results,
claim statistical certainty from a small sample, or recommend endless
polishing. Cite the decision rule and state what evidence would change it.
[PASTE AGGREGATED NUMBERS ONLY — NO USER-LEVEL DATA]
```

## P9 — run one phase (ends with a downloadable APK)

```text
Change-control: use only the assigned session branch. Never create/switch
to another branch, push to `main`, force-push, or use `git reset --hard`.
Before committing, verify author/committer identities with `git var` and
inspect the resulting commit before pushing. Use only this app repo owner's
designated address as author; no per-commit ask after designation. If none
is available, stop and ask. Keep committer identity owner-approved. Never
use AppFlow's owner-specific addresses or an agent's personal email/account.
Do not copy personal addresses into tracked app docs; author email may be
public in Git metadata.
Do not create/open a PR without the owner's explicit command in chat; PR
creation and merging are separate approvals. Work one task at a time; do
not parallelize tasks or open a second PR while any PR is open. Check the
current git/PR/CI state and do not duplicate an existing run.
Do not merge, release, publish, deploy, or dispatch an expensive/destructive
workflow without explicit authorization for that action. A code request,
branch push, or green CI is not authorization; stop at the approval gate.
Continue the [APP] plan. This repo is self-contained: obey its own rule.md
(laws, merge gate, question policy, work cycle) and read docs/ROADMAP.md and
docs/DECISIONS.md before asking or deciding anything: never re-ask a recorded
answer (that is a defect, not caution), and ask GATE items only per rule.md
§3 — each gate gets its own explicit ask, one Summary batch. Implement
**phase [N] only** — all
its 2–4 parts, no feature outside this phase; its "Done means" cell is the
acceptance test. Evidence before hypothesis: cite file:line reads against the
current tree. Reuse first: run the phase's reuse scan (frozen
knowledge/reuse-first.md) before building any part and open the phase record
with its "Reused" verdicts; log any newly shipped licence in DECISIONS.md.
Update docs with the code: set the phase's status in
ROADMAP.md, write docs/phases/NN-<slug>.md from
templates/docs-system/PHASE_RECORD.md (including what the APK shows), log any
new decision in DECISIONS.md (my answers under Owner decisions; your
reversible calls under Agent decisions, marked reversible on objection), and
update the repo's prompt.md (templates/prompt-app.md) in the same commit.
Commit and push the session branch, get CI green (including the no-device
quality gate in the frozen knowledge/fast-quality-no-device.md §1 — unit +
screenshot + lint; no physical-device test gates a phase), and confirm the
run's app-progress-apk artifact is uploaded (I must be able to download and
sideload it to see this phase's progress). Then report the run id, tip sha,
APK artifact name, and what is now visible — then PRINT THE NEXT-CHAT
PROMPT IN THIS CHAT: one fully-filled copyable text block from
templates/next-chat-prompt.md for the next phase (its parts, its verbatim
"Done means", the decisions I must never be re-asked, the CI/APK facts).
I will start the next chat by copying that block from this chat; do not
make me open GitHub, the branch, or prompt.md to get it (prompt.md is
still updated in the commit as backup only). Then stop at the merge gate.
```
