v1

## User Profile

The user uses Codex as a local Windows coding partner and wants durable outcomes that reduce future re-learning. They often ask for knowledge to be persisted into root docs, governance files, memory, or skills instead of being left in chat. They prefer agents to read the real source of truth first - live project files, active docs, routing files, database contracts, or the current site/theme - and then act.

They work on Windows PowerShell, so Windows-safe command variants matter. `pnpm.cmd` is often the right choice, shell policy friction is normal, and local-dev verification should rely on real listeners or HTTP checks rather than assuming a command worked. They like plan-first and concise by default, but want deeper structure when the task is risky, structural, or governance-heavy.

They repeatedly push for low-churn, high-signal collaboration: one canonical source instead of duplicated rule blocks, route-first cleanup instead of broad deletion, and direct execution for terse run requests. They also care about cross-agent continuity: handoff docs should be neutral/tool-agnostic, bridge files should explain folder relationships, and memory should preserve what will save future steering.

## User preferences

- When the user asks whether a rule set should be "following by codex as a principles", treat it as a high-priority behavioral layer, not a casual note.
- When the user says "ai make sure i not duplicate at this", keep one canonical source and reference it elsewhere rather than repeating long rule blocks.
- When Karpathy/final-response governance is being changed, treat the user's `Always Full` choice as strong evidence that enforcement must be real and auditable, but re-check the live Tier-0 file before deciding whether the review should be visible or internal-hidden by default.
- When the user says "Don't run too far away. Always follow my instruction. Every 2-3 minutes, re-read my original request and check if you've gone too far - if so, fall back to what I asked.", apply that as an always-on drift guard for longer tasks.
- When the user asks for root `.md` docs "so that next time ai could easily understand what i do here without research again", default to durable root documentation rather than only chat memory.
- When the user asks for docs "in a way that both ai could read", future handoff docs should stay neutral and tool-agnostic.
- When the user asks to build the database from the website project and warns not to miss `users`, `permissions`, and authorization, treat the database contract as source-of-truth first and auth/RBAC layers as must-do, not optional.
- When the user asks to clean modules "step by step", do route-first, entry-point-focused cleanup instead of broad destructive pruning.
- When the user approves keeping shared env files trackable and only ignoring local/private overrides, do not blanket-ignore all `.env*` files in that repo family.
- When the user asks for `pnpm dev` and then specifically `pnpm dev:local`, use the project's Windows-safe `pnpm.cmd` path when PowerShell blocks script execution.
- When the user says `admin-panel-angel pnpm run dev:local this`, treat that kind of terse run request as a direct execution ask, not a planning prompt.
- When the active file already points at `admin-panel-angel/apps/web-antd/.env.development.localhost`, check the matching app directory before launching.
- When building a content module with a video field, never hardcode `YouTube` in labels, placeholders, link text, or validation; use generic `Video URL` wording because the user posts TikTok and other sources.
- When working in a Vben admin panel with no real notification backend yet, disable the mock top-bar bell by default with `widget.notification: false`.
- When the user says `ai read .gemini knowledge`, treat it as a direct hydration trigger and load the bridge/index path without stopping for clarifying questions.
- When `.gemini` is being read in an active checkout, narrow the hydration to the current project context and active note instead of doing a broad crawl.
- When the user asks for cross-agent understanding of folder relationships or "full access routing", write a durable Codex-side bridge/read-order artifact instead of leaving the logic implicit.
- When no image-generation tool is available and the user still wants visuals, default to the durable free-asset fallback workflow rather than blocking on raster generation.
- When the user wants `.claudeignore`, `.geminiignore`, and `.openaiignore` aligned with `.codexignore`, standardize them together instead of treating ignore hygiene as tool-specific.
- When the user asks for "plan mode always trigger on" and also pushes for lower token cost, default to plan-first, concise-by-default behavior with deeper work only when the task is complex or risky.
- When the user wants old/useless root files removed, do root-by-root impact analysis first and only delete low-risk items directly.
- When the user wants a before/after token or speed comparison, treat measurement as part of the task rather than making vague improvement claims.
- When Codex-home skills or routing are being updated after the 2026-05-21 rename, treat `claude-app` as the live skill name and do not copy forward stale `.codex` references to `claude-frontend`.
- When deciding whether to use GitNexus, default to using it for `vben admin` / large Supabase admin projects and skipping it for websites, marketing pages, small apps, and `.codex` knowledge trees.
- When a UI request is phrased broadly as "tag design" or similar, default to a presentation-only refresh and cross-screen visual consistency before changing logic or data behavior.

## General Tips

- On long tasks, re-read the anchor request every 3-5 tool-call batches or at each phase boundary; if the work has expanded beyond the ask, fall back immediately to the last on-track state.
- `MEMORY.md` has a hard 300-line cap in current governance state; if a future consolidation pushes it over, trim the oldest task groups from the bottom while preserving the line-1 governance comment plus the top profile/preferences.
- For local PHP sites on this machine, prefer `php -S 127.0.0.1:8000 index.php`, keep it alive as a background process or user launcher, and verify with HTTP before saying it works.
- For local Vben Admin startup on Windows, prefer `pnpm.cmd run dev:local`, wait for the Vite `ready` line, and verify the actual listener / HTTP response before reporting the URL.
- On this Windows PowerShell setup, if `npm run ...` fails with `npm.ps1 cannot be loaded because running scripts is disabled on this system`, retry with `npm.cmd`.
- If Vite/esbuild fails with `Access is denied` or cannot resolve `vite.config.mts`, suspect sandbox/workspace access first rather than an app-code bug.
- For Codex-home governance work, keep `memories/0_apex/KARPATHY_TIER0_PRINCIPLES.md` as the single canonical Karpathy rule body and mirror only short contracts elsewhere.
- If routing regeneration suddenly exposes nested `.git` files, fix the ignore/router exclusions before trusting the regenerated output.
- The required Karpathy compliance checks are `Assumptions surfaced`, `Simplicity preserved`, `Surgical scope respected`, and `Verification evidence included`; the live Tier-0 file currently says they stay internal by default unless the user asks to see them or an unresolved blocker must be surfaced.
- For live `.codex` skill routing, check `2_governance/artifacts/skill_path_router.md` first; it is now the canonical trigger-to-entrypoint index and `ai claude app` maps to `skills/claude-app/WORKING_PROGRESS.md`.
- For Angel/Vben/Supabase planning, do not stop at content tables; explicitly include auth bridge, RBAC, schema-local `users` / `permissions` / `attachments`, helper functions, storage coverage, and verification of the login path [ad-hoc note].
- In this Vben/Supabase family, login/admin access is a three-layer binding across `auth.users`, `public.user`, and `{schema}.users`; if one layer is missing, login or admin flows can fail [ad-hoc note].
- Before module or SQL work on a Vben admin project backed by local Docker Supabase, prefer `docker cp` + `psql -f` over inline `psql -c`; PowerShell quoting can mangle camelCase identifiers [ad-hoc note].
- For Vben + Supabase RBAC, treat `FOR INSERT` RLS plus the matching `permissions` row as one dual-grant requirement; policy-only setups still 403.
- Storage object paths should not start with `/`, or `getStorageUrl()` can generate `//` and break previews/downloads.
- For live-data tables in this Vben/Supabase family, use corrective `ALTER` migrations instead of DROP+CREATE, and verify the next migration number against the highest existing file first [ad-hoc note].
- For Vben admin projects published against a local Docker Supabase stack through Cloudflare Tunnel, verify both `auth/v1/health` and `/rest/v1/`; `auth = 200` alone does not prove the public-backed stack is healthy [ad-hoc note].
- If `supabase stop` was run and the public DB hostname starts returning `502`, suspect the local `rest` service first and re-check `supabase status` before rebuilding or redeploying [ad-hoc note].
- In this environment, `Get-ChildItem` is the safer inventory fallback when `rg --files` hits `Access is denied`.
- Do not delete `logs_2.sqlite`, `state_5.sqlite`, or their `-wal` / `-shm` files while Codex is running.
- Use `00_CODEX_PERF_BENCHMARK.md` when the user asks for token/speed/depth comparisons; policy changes alone are not enough evidence.

## What's in Memory

### Zenius template workspace

#### 2026-05-22

- Zone 1/2/3 tag design refresh in the editable template app: zenius, template, zone tag, zone selector, HomeView.vue, StandingsView.vue, style.css, zone-tag-rail, npm.cmd
  - desc: Covers `cwd=\\?\C:\Users\user\Desktop\zenius` work to redesign the shared zone selector in `template/` while keeping behavior unchanged. Search this first for `template/` UI polish, shared chip/tag styling, or "which Zenius app is editable vs read-only?" questions.
  - learnings: The selector existed in two separate visual treatments, so both Home and Standings had to be updated together. On this machine, `npm.cmd run build` is the reliable verification path when PowerShell blocks `npm`.

### Angel Interior workspace

#### 2026-05-20

- Angel `dev:local` startup verification and Vite listener confirmation: admin-panel-angel, apps/web-antd, pnpm.cmd, dev:local, development.localhost, Vite, vite.config.mts, Access is denied, localhost:6006
  - desc: Covers `cwd=\\?\C:\Users\user\Desktop\angel-interior` follow-up work to start the Angel admin panel locally, recover from the sandbox filesystem failure, and confirm the real Vite listener. Search this first for local frontend startup, Windows PowerShell launch issues, or listener verification in this checkout.
  - learnings: The durable checks here are `pnpm.cmd`, then process/listener verification, then HTTP confirmation. `Access is denied` plus `vite.config.mts` resolution failures pointed to workspace access trouble rather than app-code breakage.

#### 2026-05-18

- Root handoff docs, database contract, and project authority: angel-interior, AI_COLLAB_PROJECT_OS.md, MASTER_PLAN.md, DATABASE.md, TABLE_STRUCTURE.md, DATABASE_MARKMAP.md, CROSSWALK.md, website-angel-interior, admin-panel-angel
  - desc: Covers `cwd=\\?\C:\Users\user\Desktop\angel-interior` root documentation and workspace authority mapping, including the shared cross-AI doc stack and the project-level docs future runs should read first. Search this first when the task is to understand the Angel workspace quickly or update its durable handoff docs.
  - learnings: `DATABASE.md` is the canonical schema/auth/RLS contract, `TABLE_STRUCTURE.md` is the quick table inventory, and `DATABASE_MARKMAP.md` is the visual mindmap layer [ad-hoc note].

- Angel Supabase recovery, admin alignment, and publish/runtime checks: Supabase, Vben, angel.users, angel.permissions, angel.attachments, auth.users, public.user, create_user, authorize, cloudflared, dist.zip, VITE_SUPABASE_URL
  - desc: Covers the recovered Angel schema contract, admin cleanup, login identity alignment, upload-ignore readiness, Cloudflare-backed publish checks, and local runtime expectations for `cwd=\\?\C:\Users\user\Desktop\angel-interior`. Search this first for `DATABASE.md` work, local DB verification, admin cleanup, or public/local stack troubleshooting.
  - learnings: The schema cannot stop at content tables; it must include auth bridge, RBAC, attachment/storage coverage, and helper functions [ad-hoc note]. Public-stack verification must include both auth and rest, and `502` usually means the local `rest` side is down [ad-hoc note].

### Codex home workspace

#### 2026-05-18

- Karpathy Tier-0 canonicalization, drift guard, and final-response compliance contract: Karpathy, Tier-0, KARPATHY_TIER0_PRINCIPLES.md, DRIFT_GUARD_PROTOCOL.md, GROUND_KERNEL.md, AGENTS.md, CODEX_DYNAMIC_ROUTING.md, compliance block, Assumptions surfaced
  - desc: Covers `cwd=\\?\C:\Users\user\.codex` governance work that made Karpathy principles an explicit Tier-0 layer, kept the detailed rule body canonical/non-duplicative, and defined the 4-check final-response contract. Search this first for Codex policy, startup/routing, drift-guard, or final-output discipline tasks.
  - learnings: The stable pattern is one canonical Karpathy file plus short mirrored contracts elsewhere. Current governance state also adds the Anchor-based drift guard for long tasks and keeps the 4-check review internal by default unless the user asks to see it.

#### 2026-05-13

- Migration away from `.gemini`, skill routing, and runtime optimization policy: .codex, .gemini, codex-router, skill_path_router, claude-app, .claudeignore, .geminiignore, .openaiignore, plan-first, 00_CODEX_PERF_BENCHMARK.md
  - desc: Covers `cwd=\\?\C:\Users\user\.codex` work to consolidate knowledge and skills into `.codex`, standardize cross-tool ignore files, restore the minimum safe skill baseline, add lean/deep runtime behavior, and keep the live skill-entrypoint map current. Search this first for Codex-home routing/governance tasks, `claude-app` vs `claude-frontend` naming, skill-completeness questions, or cleanup safety checks.
  - learnings: The durable pattern is cross-tool ignore alignment, low-token routine behavior, and a core-safe skill restore instead of bringing back every heavy optional pack. Current file state says `skill_path_router.md` is the canonical trigger map and live `.codex` routing should use `claude-app`, not stale `claude-frontend` wording.

### Older Memory Topics

#### EcoWorld checkout

- Project-root cleanup and shared PHP asset cache busting: EcoWorld, tmp, test-results, cdp-profile, htmlHead.php, htmlBody.php, init.php, ECO_ASSET_VERSION, php -l
  - desc: Covers `cwd=\\?\C:\Users\user\Desktop\ecoworld` cleanup of disposable root artifacts plus shared PHP cache-busting for CSS/JS includes. Use this for EcoWorld cleanup requests, stale asset reload complaints, or shared PHP layout asset handling.

- `.gemini` routing hydration for EcoWorld website context: ai read .gemini knowledge, EcoWorld, ECOWORLD_IMPLEMENTED_UI_NOTES_2026-05-12.md, GEMINI_DYNAMIC_ROUTING.md, Update-GeminiRouting.ps1, ROUTER.idx, ATLAS.idx
  - desc: Covers the successful `ai read .gemini knowledge` hydration flow in `cwd=\\?\C:\Users\user\Desktop\ecoworld`, including the bridge read order, router refresh, fallback indexes/kernels, and loading the active EcoWorld UI note. Use this when EcoWorld tasks need `.gemini` context loaded quickly without broad tree reads.

- Free visual asset fallback and homepage filter/search refresh: EcoWorld, FREE_VISUAL_ASSET_SOURCING.md, Unsplash, Pexels, Pixabay, Material Symbols, SVG, CSS art, filter-panel, information.txt
  - desc: Covers `cwd=\\?\C:\Users\user\Desktop\ecoworld` work for the "no image-generation tool available" fallback plus the brand-grounded homepage filter-panel refresh. Use this for asset-sourcing policy, persisted image workflow updates, or UI polish that must stay true to the live EcoWorld design language.

#### Windows Codex home / `.gemini` bridge

- Codex `.gemini` full access routing and auto-refresh: .gemini, .codex, GEMINI_FULL_ACCESS_ROUTING.md, GEMINI_DYNAMIC_ROUTING.md, ROUTER.idx, ATLAS.idx, Update-GeminiRouting.ps1, SESSION_SHADOW.json
  - desc: Covers building a Codex-side bridge so the assistant can understand and reuse `.gemini` knowledge, memory, and skills, plus a manifest-based dynamic router and watcher that refreshes Codex-owned routing artifacts when safe `.gemini` files change. Use this for Windows Codex-home work that needs folder relationship mapping, `.gemini` read order, skill conversion boundaries, or refresh automation.
