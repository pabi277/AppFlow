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
