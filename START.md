# Start a new app repository

**Law:** a new app repository takes data from the public playbook BEFORE any
app code. Pin a full commit SHA. The copied files are a frozen snapshot, not a
submodule.

## 0. Research and select the app idea

Before creating an app repository, use `PROMPTS.md` P1 to research and present
3–5 evidence-backed app options. Compare their user need, competition, owner
advantage, four-week scope, and policy/privacy/monetization risks. The owner
chooses, combines, or refines an option; stop before repo creation or app code
until the owner explicitly selects a direction. After the Play title is
confirmed, update the central `APP_LIST.md`; do not copy that portfolio list
or AppFlow-specific identity details into the new app repository.

## GitHub authority rule

- Use only the assigned working branch. Never create/switch branches, push to
  `main`, force-push, or discard work with `git reset --hard`.
- Before committing, verify author/committer identities with `git var` and
  inspect the resulting commit before pushing. For AppFlow, an author address
  listed in `RULES.md` is pre-authorized; no per-commit ask. Keep committer
  identity owner-approved. Never use an agent's personal email/account or copy
  AppFlow's addresses into a new app repo. For other repos, use only that
  repository owner's designated address; if none is available, stop and ask.
  Do not rewrite pushed history without separate permission.
- Do not create/open a PR without the owner's explicit command in chat. Do not
  merge without separate explicit authorization. A request to code, a branch
  push, or green CI does not authorize a PR or merge.
- Work one task at a time; do not parallelize tasks or open a second PR while
  any PR is open. Check the branch, working tree, PRs, and CI before actions;
  do not duplicate an existing PR or run.
- Do not release, publish, deploy, or dispatch an expensive/destructive action
  without explicit permission. Stop at the approval gate.

## 1. First message in the new session

Paste this exact template as the first message, replacing only `<SHA>` with
the full commit SHA you selected:

```text
Before any code: read the public playbook repo https://github.com/pabi277/AppFlow at commit <SHA> and follow its START.md.
```

## 2. Snapshot and commit before app code

From the root of a new, otherwise-empty app repository, replace only the
placeholder with a full 40-character AppFlow commit SHA. The source URL below
is the real AppFlow repository. These commands copy only `templates/` and
`knowledge/`, verify the checked-out commit, write provenance, and commit the
snapshot; they do not create a submodule.

```sh
set -eu
PLAYBOOK_URL='https://github.com/pabi277/AppFlow.git'
PLAYBOOK_SHA='<SHA>'
TMP_DIR="$(mktemp -d)"

git clone --quiet "$PLAYBOOK_URL" "$TMP_DIR/playbook"
git -C "$TMP_DIR/playbook" checkout --quiet --detach "$PLAYBOOK_SHA"
test "$(git -C "$TMP_DIR/playbook" rev-parse HEAD)" = "$PLAYBOOK_SHA"

if [ -e templates ] || [ -e knowledge ]; then
  echo 'Refusing to overwrite an existing snapshot.' >&2
  exit 1
fi
cp -R "$TMP_DIR/playbook/templates" ./templates
cp -R "$TMP_DIR/playbook/knowledge" ./knowledge

if [ ! -f README.md ]; then
  printf '# YOUR_APP_NAME\n\n' > README.md
fi
if grep -Fq 'Bootstrapped from AppFlow @' README.md; then
  echo 'README already has provenance; do not append it twice.' >&2
  exit 1
fi
printf '\nBootstrapped from AppFlow @ %s on %s\n' \
  "$PLAYBOOK_SHA" "$(date -u +%F)" >> README.md

git add templates knowledge README.md
git commit -m "Bootstrap playbook snapshot $PLAYBOOK_SHA"
rm -rf "$TMP_DIR"
```

The README provenance line must read:

```text
Bootstrapped from AppFlow @ <sha> on <date>
```

Keep it when you later fill the app README. Keep the copied snapshot unchanged;
update it only through a deliberate, documented refresh commit.

## 3. Only after the snapshot commit

1. Fill `templates/readme-app.md` and use it as the app's `README.md`, keeping
   the provenance line.
2. Create the app's own root `LICENSE` (MIT or GPL-3.0) before app code; do not
   mistake the playbook's mixed license notice for the app's license.
3. Create the smallest Gradle skeleton and a hello screen.
4. Copy `templates/ci-build.yml` to `.github/workflows/ci-build.yml`; wire the
   owner's signing secrets by name, never by committing secret values.
5. Get CI green (unit tests and signed release artifacts).
6. Write a short `DECISIONS` log, then implement app code under `RULES.md`.

## 4. Pre-code checklist

Any **NO** or unchecked item blocks coding. Keep personal tester details
outside Git.

- [ ] Play account exists? Account type and required production-access steps
      are understood.
- [ ] testers-clock running? The 25-person opt-in plan and a dated start plan
      are ready. The Play 14-day clock starts only when a closed-test build is
      live and real testers opt in; never claim it started early.
- [ ] Evidence-backed app options were presented and the owner explicitly
      selected a direction before repo creation?
- [ ] Niche verdict line written? Use `knowledge/niche-method.md`.
- [ ] License chosen? MIT or GPL-3.0, with the app's license template ready.

For eligible personal Play accounts created after 2023-11-13, the current
closed-test gate is at least 12 continuously opted-in testers for 14 days.
Recruiting 25 genuine volunteers is a buffer, not a claim that Play requires
25 or 20. Verify the current rule in Play Console before starting the clock.
