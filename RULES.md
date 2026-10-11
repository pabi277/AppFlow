# Rules

1. Discuss → decide → code; no edit before permission.
2. Diagnose first; evidence before proposals.
3. Ship small: idea → published ≤ 4 weeks or kill.
4. Kill fast: flat retention/downloads after the first weeks → next app.
5. One repo per app; one monetization model per app; apps must be genuinely different products (no reskins — Play's repetitive-content policy).
6. Modern `targetSdk` (current Play requirement) from day one; minSdk sane; never inherit CodeC's target-28 exception.
7. License every app repo (MIT or GPL-3.0) before first publish.
8. Privacy policy + Data Safety filled truthfully; declare AdMob.
9. Respectful ads: rewarded-first; interstitials only at natural breaks; never surprise-placement; ad-free IAP always offered.
10. Account is the crown jewel: one clean Play account forever; never fake reviews, never click-fraud, never multiple accounts, never shady ad networks.
11. CI is the PC: nothing ships without green CI (build + tests + signed artifact).
12. Docs ride with code: every app repo keeps a short DECISIONS log.
13. No backend unless the niche proves it; offline-first default.
14. Content accuracy is the human's job (agent accelerates, owner verifies).

## Policy checkpoint

As checked on 2026-10-10, Google Play requires new mobile apps and app
updates to target Android 16 / API 36 or higher. Re-check the live [target API
policy](https://support.google.com/googleplay/android-developer/answer/11926878?hl=en)
before every release; this number changes over time.

Implementation note: treat the required ad-free IAP as the one opt-out
exception alongside one primary monetization model—not as permission to stack
multiple ad-driven or paid mechanics.

## App discovery and Play Store registry

- The owner does not have to arrive with an app idea. For every new app, the
  agent researches and presents 3–5 differentiated options with linked, dated
  evidence on user need, competitors/reviews, owner advantage, four-week
  offline-first scope, monetization, privacy, and policy risks.
- Compare and recommend; do not decide for the owner. The owner may choose,
  combine, or refine an option. Do not create an app repository or write app
  code until the owner explicitly selects a researched direction.
- Maintain `APP_LIST.md` as the portfolio register. Record the exact official
  Google Play title only when confirmed in Play Console or on the live listing;
  include package ID, listing URL, status, and verification date. Never invent
  an official title or put working-name guesses in the official-name field.

## Questions: ask less, gate always

Full policy: [PLAN.md](PLAN.md) §3. Three classes:

- **GATE — always ask, never act without an explicit yes:** repo creation,
  app name + package ID, git author identity, license if unfixed, PR / merge /
  `main` push / release / publish / deploy / Play submission, money, legal or
  tax actions, waiving a law above, changing a recorded decision. One Summary
  batch per gate moment, ≤4 questions.
- **DECIDE-ONCE — ask once in the plan chat, record in `DECISIONS.md`:**
  product-shaping choices (languages, monetization, scope, time budget).
  Re-asking a recorded answer is a defect.
- **DEFAULT — never ask:** researchable facts (research and cite), reversible
  choices (decide and log under Agent decisions), anything already answered.

## GitHub authority and approval gate

These process rules supplement the 14 laws above; they do not change their
wording. They adapt the owner-approval rules in CodeC's [`rule.md` §§2–4](https://github.com/pabi277/CodeC/blob/5cbc1c0a394b810e22928d247649ee2c2cb1bba3/rule.md)
and its [README contributor guidance](https://github.com/pabi277/CodeC/blob/5cbc1c0a394b810e22928d247649ee2c2cb1bba3/README.md),
checked on 2026-10-10 at CodeC main commit
`5cbc1c0a394b810e22928d247649ee2c2cb1bba3`. CodeC-specific product
invariants are not imported into AppFlow.

- **Branch discipline:** work only on the assigned current session branch. Never
  create or switch to another branch, push to `main`, or use `git push --force`.
  Commit and push only to the assigned branch when the requested work calls for
  it. Never use `git reset --hard`; protect existing work.
- **Commit identity and attribution:** GitHub contributor attribution comes
  from commit metadata, not simply push authentication. Before committing,
  verify `git var GIT_AUTHOR_IDENT` and `git var GIT_COMMITTER_IDENT`; inspect
  the resulting commit before pushing.
  Owner-approved author addresses for this AppFlow repository:
  - `chakraborttypabi2772006@gmail.com`
  - `pabitra27.7.06@gmail.com`
  Either is pre-authorized as `GIT_AUTHOR_EMAIL`; no per-commit approval is
  needed. Keep `GIT_COMMITTER_EMAIL` on the owner's approved GitHub noreply or
  bot identity. Push through the connected GitHub authentication; these email
  addresses are not push credentials. Never use an agent's personal email or
  GitHub account. Do not repeat these addresses in other tracked docs, templates,
  or new app repositories. The selected author address is public in Git metadata.
  Do not rewrite already-pushed history to alter attribution without separate
  permission.
- **PR approval:** do not create or open a pull request without the owner's
  explicit command in chat. Do not merge without a separate explicit command.
  Permission to edit, commit, push a branch, or obtain green CI is **not**
  permission to create a PR or merge it. “Open a PR” does not mean “merge it.”
- **Release approval:** do not push to `main`, tag a release, submit to Google
  Play, publish an artifact, or deploy a site/package without explicit owner
  authorization.
- **One task at a time:** do not parallelize tasks or create a second PR while
  any PR is open. Check the current branch, working tree, PRs, and CI runs
  before GitHub actions; do not duplicate an existing run.
- **Expensive/destructive actions:** do not dispatch these workflows, releases,
  or device tests without explicit confirmation. A green check is evidence, not
  release or merge authorization.
- **Stop and report:** provide verified branch/commit/check status and stop at
  the approval gate whenever the next action has not been explicitly authorized.
