# Pre-launch security review — Android-first AppFlow apps

> A practical, evidence-based gate adapted from the owner-provided *Pre-Launch
> Security Audit* (v2.0, Nov 2026; reviewed 2026-11-16). Its original
> Emergent/React/FastAPI/MongoDB/Expo assumptions are **not** AppFlow defaults;
> verify the actual app stack and run only applicable checks. This is a first-pass
> review, not a penetration test or a claim that an app is "secure".

## Four-step review

1. **Intake:** read the whole app and identify its actual product type, data,
   Android client, backend, auth, payments, AI, and uploads. Summarize what is
   detected; ask only for unknown facts (live status, target countries/audience,
   third-party code, account settings). Never assume Emergent or a web stack.
2. **Code pass:** run every applicable check below without pausing between
   checks. Record evidence in the private report; mark skipped checks N/A with
   a reason and hidden/live settings CAN'T VERIFY. Then present counts and a
   concise severity-grouped summary, asking which proposed fixes are approved.
3. **Fix round:** make only approved fixes, Critical first; use the smallest
   root-cause change. Re-run each check and relevant tests; list what remains
   open and anything that must be repeated manually on live (secret/config/data
   changes), without declaring that complete yourself.
4. **Owner checklist/report:** send one compact list of owner-only checks and
   an honest final status: passed, fixed, open, need owner verification, and
   skipped. Never call the app "secure" or "100% safe".

## When and how

- Plan the review in the release-readiness phase, before the first production
  submission. Repeat before major releases and after adding accounts, payments,
  uploads, AI, a backend, or a new sensitive SDK; review at least quarterly for
  a live app.
- Read the app's source and build configuration first; list detected app type,
  data flows, permissions, network services, auth, billing, ads, AI, uploads,
  and release targets. Confirm only facts code cannot reveal. Do not assume a
  backend or user accounts exist.
- Read-only by default. Do not probe third-party systems, production users,
  or services the owner does not own. No destructive tests, load floods, real
  payments, or real messages. Use local/CI, preview, or staging and test data.
- Do not print or request credentials, tokens, signing material, tester details,
  or full personal data. Mask any accidental secret in evidence; if a key may
  have leaked, recommend revocation/rotation without asking the owner to paste it.
- Findings need evidence: file:line, manifest/config, CI output, or named
  owner-confirmed fact. Label **Confirmed**, **Suspected**, or **CAN'T VERIFY**;
  never mark an unseen live setting PASS. Record N/A checks and why.
- A report that lists exploitable weaknesses is private working material: create
  `SECURITY-AUDIT.md` only after adding it to `.gitignore`; never commit, publish,
  put it in a served directory, or include secrets. Share a short masked summary
  in chat. After fixes and verification, delete the private report; retain only
  a non-sensitive completion summary and unresolved issue IDs in phase/release
  notes. Do not erase the owner's original files or evidence without permission.
- Propose fixes, grouped Critical/High/Medium/Low. Change only fixes the owner
  approves (or work explicitly included in the current phase); make the smallest
  root-cause change, never weaken a guardrail. Re-run each check and relevant
  tests. No production submission while a Critical/High finding remains open.
  If something cannot be checked, state the exact owner action that would verify it.

## Code and build checks — run those that apply

### 1. Secrets and release artifact

- Search current source, configuration, generated artifacts, and Git history
  for private keys, backend credentials, signing secrets, and unrestricted
  service tokens. A client identifier that is intentionally public is not a
  secret; verify its restrictions. Removing a committed key is insufficient:
  treat it as exposed and recommend revoking/rotating it.
- Secrets are injected through CI/release secret stores, not source, logs,
  prompts, crash reports, analytics, or the APK/AAB. Inspect the **release**
  artifact for debug endpoints, staging URLs, test ad IDs, debug menus, verbose
  logs, and accidental secrets; confirm R8/minification settings as intended.
- Protect signing keys and backups; inspect secret names/permissions, never
  secret values. Report account MFA and recovery as owner checklist items.

### 2. Identity, authorization, data, and input (only if present)

- Map every screen, route, worker, deep link, and backend endpoint that reads or
  changes private data. Enforce access control at the trusted boundary, not by
  hiding UI. For multi-user data, verify ownership/team scope on every read,
  update, and delete; role/plan/credit fields cannot be self-assigned.
- Passwords are salted and purpose-built hashed if the app owns them. Tokens
  are verified and expire; logout/revocation behavior is defined. Store device
  credentials in Android Keystore-backed storage; avoid plaintext preferences,
  logs, or backups. Do not add login without evidence of need.
- Validate types, lengths, ranges, and allowed values at trusted boundaries;
  use parameterized queries and safe serialization. Render untrusted content
  safely; errors must not expose stack traces, filesystem paths, tokens, or
  other users' data. Restrict upload type/size and keep private files private.
- For URLs fetched by a backend, assess SSRF, redirects, DNS/IP validation,
  timeouts and response-size bounds. For local/deep-link inputs, validate
  schemes, hosts and parameters; never trigger sensitive changes without auth
  and explicit confirmation.
- If there is a database/storage or backend, review access policies, network
  exposure, backups/restore, least privilege, pagination, rate limits and safe
  error handling. If Supabase/Firebase is used, check rules/RLS (not test-mode
  public access); if unavailable to inspect, say CAN'T VERIFY.

### 3. Android platform and app links

- Manifest permissions are minimal, justified, requested at the point of use
  when appropriate, and explained to the user. Review exported activities,
  services, receivers, providers, intent filters, pending intents and
  FileProvider paths for least privilege and safe validation.
- Network traffic uses HTTPS; no broad cleartext exception. Review network
  security config, certificate/debug overrides and WebViews. WebViews load
  only trusted origins; JavaScript bridges are minimal and disabled for
  untrusted content.
- Deep links/app links validate host, scheme and parameters; they do not let an
  unauthenticated link perform payments, account changes, file access or
  deletion. Sensitive operations require authentication and confirmation.
- Check backup/data-extraction rules, clipboard/sharing, screenshots/notifications
  and local storage for unintended exposure of sensitive data.
- Release build uses production configuration; debug/test screens and test
  endpoints are off. Inspect merged manifest and final APK/AAB, not only source.

### 4. APIs, billing, ads, and AI (only if present)

- Rate-limit costly or abuse-prone operations at the trusted server/account
  boundary where available. Bound input/output, timeouts, retries and work;
  avoid unbounded polling or spend. Do not trust client-supplied price,
  entitlement, balance, role, or user identity.
- Google Play Billing purchases are verified using current official guidance;
  entitlement is granted once, restored correctly, and handles cancellation,
  refund, pending and failure states. Never use a success screen alone as proof.
  Use test purchases until the owner authorizes live billing configuration.
- Ads use official SDKs, correct test units in development, policy-compliant
  placements and consent/disclosure where required. Do not click live ads or
  test live units yourself.
- If AI exists: cap per-user/total usage, input and output size and time; treat
  retrieved/user content as untrusted instructions; scope tools to the user's
  data and require confirmation for destructive/costly actions. Escape output;
  never execute model output as code, shell commands, SQL or authorization.
  Keep provider keys and sensitive data out of client code and prompts.
- Verify payment/webhook signatures and idempotency on server-controlled
  integrations. Do not run real transactions during audit.

### 5. Dependencies, privacy, and operations

- Review direct/transitive dependency versions, licences, known vulnerabilities,
  release provenance, install scripts and unnecessary permissions/trackers.
  Use lockfiles/version pins and a CI vulnerability check where practical;
  never force-upgrade blindly. Inspect imported repositories/templates for
  unexpected agent instructions or commands seeking secrets/exfiltration.
- Minimize collected data, retention and sharing. Privacy policy, Play Data
  Safety, audience/content declarations and SDK disclosures must match the
  shipped build. No account creation means account-only checks are N/A; do not
  invent features to satisfy a checklist.
- Review logs/analytics for secret or personal-data leakage and make sure
  security-relevant events can be diagnosed without recording credentials.
  Check availability of backups, restore path, error alerts and incident contact
  as owner-confirmed operational items.
- Ask the owner privately to confirm MFA, secret rotation, spending limits,
  budget alerts, backup restore, and account recovery; never request passwords,
  recovery codes, or actual keys. Record unanswered operational checks as
  CAN'T VERIFY, not PASS.
- Owner checklist (ask only applicable items): rotate any key ever pasted into
  chat/support or committed publicly; enable MFA on GitHub, Play, billing,
  domain, email, and backend accounts; set spending caps/alerts; verify backup
  and restore; use two separate test accounts to check data isolation when
  accounts exist; remove unnecessary collected data; keep test data out of
  production; confirm incident/error alerts and rollback; verify audience,
  privacy, Data Safety and current regional/child-safety duties with the owner.
  Ask yes/no or for evidence that contains no credentials or tester personal
  data. Legal/compliance interpretations remain owner-reviewed, not agent
  guarantees.

## Audit report and exit

Keep the private working report concise and repeatable:

```text
# SECURITY-AUDIT.md (private, ignored; delete when remediation is complete)
Scope: app/build/version, detected stack, what was skipped and why
Summary: N passed · N failed · N need owner verification · N not applicable
## Findings
[ID] Check: PASS / FAIL / NOT APPLICABLE / CAN'T VERIFY
Severity (FAIL): Critical / High / Medium / Low
Evidence: file:line or config; masked · Confirmed / Suspected
Checked: exact routes/files/components/artefacts covered
Risk: plain-language impact
Fix: proposed change · owner-approved? · verification evidence/status
```

At completion, report counts, open findings, exact owner-only follow-ups, and
what was re-tested. Never claim "100% secure". Record in the public phase
record only the review date, scope, counts and safe unresolved IDs—not
exploit details, secrets, or personal data. A professional security review is
needed before handling payments or sensitive data at scale.

---


Source note: adapted from the owner-uploaded *Pre-Launch Security Audit* by
Mayank Shah, v2.0 (Nov 2026). Its source list includes
[OWASP Top 10: 2025](https://owasp.org/Top10/2025/) and the
[OWASP Top 10 for LLM Applications](https://genai.owasp.org/llm-top-10/);
verify current guidance and applicable law before each release.
