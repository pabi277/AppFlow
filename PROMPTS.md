# Copy-paste prompt library

Replace bracketed fields before sending. Each prompt assumes the app repo has
already frozen `templates/` and `knowledge/` from a pinned playbook commit.
Do not paste secrets, account IDs, tester contacts, or real ad IDs into prompts.

## P1 — niche validation

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
Validate [NICHE] for [COUNTRY / LANGUAGE / AUDIENCE] before any code. Follow
knowledge/niche-method.md. Seed from the owner's real experience; search Play
for the exact phrase a user types; record the query, country, date, and links;
open the top five relevant listings; record rating and last update; read ten
1-star reviews per relevant listing and turn verified complaints into needs.
Use 3.5–4.2 stars and updates older than one year as signals, not proof. Decide
whether the market is crowded-but-bad, empty, or dominated by a giant. Check
whether the owner has a real niche advantage and verify incumbent ad friction
by using the apps, not by guessing from store pages. Cite evidence and
uncertainty. Output one verdict line in this format:
Demand: [...]; staleness: [...]; complaints: [...]; owner advantage: [...].
Then give the top three 1-star complaints as a concrete, testable v1 spec.
Do not write code. If evidence is insufficient, say what to inspect next.
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
Before app code, read the public playbook at [PLAYBOOK_URL] and pinned commit
[PLAYBOOK_SHA]. Follow its START.md. Copy templates/ and knowledge/ into this
new repo as frozen files, add the provenance line to README.md, and commit
that snapshot first. Then fill templates/readme-app.md as README.md, choose
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
Android v1 for [NICHE]. Keep source data in versioned assets (no backend or
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
