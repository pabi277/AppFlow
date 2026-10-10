# Maintenance

Keep this playbook useful on a phone: short markdown, plain links, no build
step, and no copied credentials or personal data. The owner-approval and
commit-identity gates in `RULES.md` apply to maintenance too: a review, branch
push, or green CI does not authorize a PR, merge, release, publication, or
deployment. For AppFlow commits, use an author address listed in `RULES.md`
and an owner-approved committer identity. Never reuse AppFlow's addresses in
app templates or a new app repository.

## Quarterly playbook review

- Re-check links, target API policy, testing gates, store asset rules, ad SDK
  lifecycle, tax/payment notes, and GitHub Actions examples.
- Search for changed Google Play and AdMob requirements; update dated claims
  and their sources, not just wording.
- Verify every internal link and confirm the required files still exist.
- Read `RULES.md` for contradictions and keep each law unchanged unless the
  owner deliberately decides otherwise.
- Record a new full commit SHA for future app bootstraps. Existing app repos
  stay pinned to their frozen snapshot until explicitly refreshed.

## Annual full audit

- Re-run the phone-first bootstrap dry run described in `START.md`.
- Review license boundaries: prose outside `templates/` is CC BY 4.0;
  template files carry the MIT header.
- Inspect every workflow for permission scope, secret handling, action versions,
  signing output paths, and safe behavior on pull requests.
- Re-read privacy, Data Safety, tester, and ad guidance against current official
  documentation. Remove stale examples rather than guessing.
- Check that the repository contains no real keys, account IDs, AdMob IDs,
  private tester details, or other personal data.

## Each app, every year (and before a Play deadline)

- Check the app's target API requirement and migrate early; build, test, and
  publish a signed update before the applicable deadline.
- Update Gradle, AGP, JDK, Android SDK, and libraries deliberately; run unit
  tests and test the release build on real devices.
- Review permissions, offline behavior, privacy policy, Data Safety answers,
  SDK disclosures, content rating, and screenshots against the shipped build.
- Test ad consent, ad placements, ad-free purchase, restore, and offline paths.
- Check signing-key backup/recovery and GitHub secret access without putting
  credentials in Git or chat.
- Keep a short `DECISIONS` log: what changed, why, evidence, owner, and date.
- Reply to recent reviews respectfully; verify facts and never request a
  positive rating.

The Playbook's yearly target is an audit, not permission to wait a year when
Google changes a policy or a security issue needs faster action.
