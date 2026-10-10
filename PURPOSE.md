# Purpose

## Mission

Give one producer profile a calm, repeatable path from idea to published
Android app: an Indian indie developer with no PC, working on a phone in
CodeC with an AI agent, using GitHub Actions to build and Google Play to
ship.

This repository is the playbook, not an app. Every future app starts by
reading a pinned playbook commit and importing frozen copies of `templates/`
and `knowledge/` before any app code exists.

## Constraints

- Phone-first: do not assume a desktop IDE or local Android build.
- GitHub Actions is the build machine; CI must test and sign release outputs.
- Keep the first version small enough to publish or kill within four weeks.
- Prefer static bundled data and offline-first behavior; add a backend only
  when observed user need proves it necessary.
- Use current Play requirements, not a stale SDK value inherited from CodeC.
  As checked on 2026-10-10, new mobile apps and updates must target Android
  16 / API 36 or higher from 2026-08-31; check the live policy before release.
- Keep credentials, account identifiers, signing keys, service-account JSON,
  tester contact lists, and real AdMob IDs out of this playbook.
- GitHub control is owner-gated: no PR, merge, `main` push, release, Play
  submission, or deployment without explicit permission in chat.
- An email explicitly designated by the owner may be used only as commit-
  author metadata; never use an agent's personal email/account or copy personal
  addresses into tracked docs. Keep the committer identity owner-approved.
- The owner verifies facts, legal/tax choices, app content, and final releases.

## Money model

Pick one primary monetization model per app. Prefer optional rewarded ads
where a user knowingly asks for a reward; never interrupt a task. Rule 9 also
requires a clearly offered ad-free one-time purchase. Treat it as the single
opt-out path, not an excuse to layer subscriptions, paywalls, and ad loops.

The ₹49–99 ad-free price is a starting experiment, not a promise of sales or
profit. Set and localize the actual price in Play Console. For digital app
functionality such as an ad-free version, use Google Play Billing unless a
current, applicable program or policy exception says otherwise.

AdMob earnings are not a salary forecast. The USD payment threshold is
$100 for a USD account; other account currencies have their own thresholds.
Only finalized earnings count, and holds or payment setup can delay payment.
Check the current payment profile and thresholds.

## Anti-goals

- No app factory, reskin portfolio, or keyword-stuffed clones.
- No backend, login, analytics, or permissions without a proven user need.
- No deceptive, surprise, or forced ad placements; no fake reviews or clicks.
- No purchased testers, review swaps, shady ad networks, or account tricks.
- No claims that an app guarantees an exam result, income, or legal outcome.
- No agent-authored facts shipped without human source-checking.

## Policy sources checked

- [Google Play target API requirements](https://support.google.com/googleplay/android-developer/answer/11926878?hl=en)
- [Google Play Payments policy](https://support.google.com/googleplay/android-developer/answer/10281818?hl=en)
- [AdMob payment thresholds](https://support.google.com/admob/answer/2772208?hl=en)
