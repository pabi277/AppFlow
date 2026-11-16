# Phone-First Indie Playbook
One source of truth for a phone-first Indian indie developer shipping Android apps.
Build on a phone with CodeC and an AI agent; use GitHub Actions as the build machine.
Keep apps small, offline-first, distinct, respectful, and time-boxed to four weeks.
Every new app starts from a pinned playbook commit—not from app code.
Bootstrap: start each new app with [common-prompt.md](common-prompt.md) (once
per app), then use [START.md](START.md); log official Play names in
[APP_LIST.md](APP_LIST.md).
Read [PURPOSE](PURPOSE.md), [RULES](RULES.md) (approval/identity), [PLAN](PLAN.md)
(plan-only first chat; ask less, gate always), and [PROMPTS](PROMPTS.md).
After the app idea is selected, compare 2–3 India Play Store listings and have
the owner use a free official-listing comparator. Its screenshots are temporary
private context: never commit them. Keep only clean-room notes in GitHub and
ignored workspace copies through all UI implementation phases; remove the
copies after final UI approval. Complete the applicable
[pre-launch security review](knowledge/pre-launch-security-audit.md) before
production. Build reuse-first: [knowledge/reuse-first.md](knowledge/reuse-first.md)
(research open source before building anything), the verified catalogue in
[knowledge/open-source-references.md](knowledge/open-source-references.md), and
the best-way build reference [knowledge/app-engineering.md](knowledge/app-engineering.md),
and [knowledge/fast-quality-no-device.md](knowledge/fast-quality-no-device.md)
(quality proven in CI without device tests, fast builds, and the next-chat
prompt printed in chat at every phase end). Design UI on the web after the
comparator handoff: [knowledge/ui-reference-site.md](knowledge/ui-reference-site.md)
(workflow + approval gate) with stacks from
[knowledge/web-ui-references.md](knowledge/web-ui-references.md). Verify live
Play and AdMob requirements before each release; policies change.
Prose outside `templates/`: CC BY 4.0; `templates/`: MIT (see [LICENSE](LICENSE)).
Review quarterly; see [MAINTENANCE.md](MAINTENANCE.md) for upkeep.
