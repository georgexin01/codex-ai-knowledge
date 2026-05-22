<!-- AI GOVERNANCE: MAX 300 LINES. When adding new task groups, trim oldest from bottom. Auto-trim fires on rot-audit when line count exceeds 300. -->

## User Profile

The user uses Codex as a local Windows coding partner and prefers durable outcomes that future agents can reuse without re-learning the setup. They often ask for workflows persisted into root docs, governance notes, memory, or skills rather than left as chat-only guidance. Environment is Windows PowerShell - use `pnpm.cmd`, Windows-safe fallbacks, and expect permission/policy friction. They prefer plan-first and concise by default, deep and explicit when the task is risky or structural. They care about token efficiency: read the real thing first, then act.

## Key Preferences

- Treat any rule set asked to "follow as principles" as a high-priority behavioral layer.
- Keep one canonical source; reference it elsewhere - never repeat long rule blocks.
- Default to durable root docs over chat-only guidance when the user asks to persist knowledge.
- Handoff docs must stay neutral and tool-agnostic ("in a way that both ai could read").
- Treat DB contract as source-of-truth first; auth/RBAC layers are must-do, not optional.
- Route-first, entry-point-focused cleanup - never broad destructive pruning.
- Never blanket-ignore all `.env*` files; only ignore local/private overrides.
- Use `pnpm.cmd` on Windows when PowerShell blocks plain `pnpm` script execution.
- Terse run requests ("admin-panel-angel pnpm run dev:local this") = direct execution, not planning.
- Never hardcode platform names (YouTube) in video fields; use generic "Video URL".
- Disable mock notification bells in Vben panels with no real backend (`widget.notification: false`).
- `ai read .gemini knowledge` = direct hydration trigger - no clarifying questions.
- Route `.gemini` reads to current project context + active note, not a broad crawl.
- Cross-agent knowledge reuse -> write a durable bridge/read-order artifact in `.codex`.
- Default to free-asset fallback workflow when no image-generation tool is available.
- Align `.claudeignore`, `.geminiignore`, `.openaiignore` with `.codexignore` together.
- Plan-first + concise by default; deep only when complex/risky or explicitly requested.
- Re-read the user's original request every 2-3 minutes / 3-5 tool batches on long tasks; if scope drift appears, fall back to the anchor.
- Restore core-safe skill baseline rather than every heavy optional pack.
- Root-by-root impact analysis before deleting root files; only remove low-risk items directly.
- Treat before/after token or speed comparison as part of the task, not a vague claim.
- GitNexus: use first for vben admin / large Supabase projects; skip for websites and small apps.

# Task Group: Codex Tier-0 Karpathy governance and routing enforcement
scope: Reuse when the task changes Codex behavioral governance, startup/routing contracts, or final-response discipline; especially relevant when the user wants Karpathy rules treated as enforceable Tier-0 policy without duplicated rule bodies.
applies_to: cwd=\\?\C:\Users\user\.codex; reuse_rule=safe for this user's Codex-home governance workspace if you re-check the live Tier-0 files, generated routing output, and ignore/router exclusions before editing

## Task 1: Canonicalize Karpathy Tier-0 principles without duplication, success

### rollout_summary_files

- rollout_summaries/2026-05-18T03-53-04-26nW-karpathy_tier0_strict_enforcement_layer.md (cwd=\\?\C:\Users\user\.codex, rollout_path=C:\Users\user\.codex\sessions\2026\05\18\rollout-2026-05-18T11-53-04-019e3937-4690-7373-916c-c08785057744.jsonl, updated_at=2026-05-18T04:29:13+00:00, thread_id=019e3937-4690-7373-916c-c08785057744, created the canonical Tier-0 Karpathy file and rewired startup/routing references)

### keywords

- Karpathy, Tier-0, KARPATHY_TIER0_PRINCIPLES.md, GROUND_KERNEL.md, AGENTS.md, CODEX_DYNAMIC_ROUTING.md, router-config.json, .codexignore, .openaiignore, .claudeignore, Update-CodexRouting.ps1, non-duplicative

## Task 2: Enforce the 4-check Karpathy compliance contract, later refined to internal review by default, success

### rollout_summary_files

- rollout_summaries/2026-05-18T03-53-04-26nW-karpathy_tier0_strict_enforcement_layer.md (cwd=\\?\C:\Users\user\.codex, rollout_path=C:\Users\user\.codex\sessions\2026\05\18\rollout-2026-05-18T11-53-04-019e3937-4690-7373-916c-c08785057744.jsonl, updated_at=2026-05-18T04:29:13+00:00, thread_id=019e3937-4690-7373-916c-c08785057744, added the strict final-response contract and validated it with prompt-output simulations)

### keywords

- compliance block, always full, internal review hidden by default, Assumptions surfaced, Simplicity preserved, Surgical scope respected, Verification evidence included, pass | fail | n/a, Response Footer Requirement, karpathy-guidelines

## User preferences

- when the user asked whether the Karpathy principles must be "following by codex as a principles", treat them as a high-priority behavioral layer, not a casual note [Task 1]
- when the user said "ai make sure i not duplicate at this", keep one canonical source and reference it elsewhere rather than repeating long rule blocks [Task 1]
- when the user selected `Always Full` for enforcement, they signaled that Karpathy compliance must be explicit and enforceable rather than a casual suggestion; for similar future governance changes, confirm visible-vs-hidden output mode early because the live Tier-0 file can later refine the rendering contract [Task 2]
- when the user says "Don't run too far away. Always follow my instruction. Every 2-3 minutes, re-read my original request and check if you've gone too far - if so, fall back to what I asked.", treat that as an always-on drift-guard rule for longer tasks and re-anchor silently at tool-batch / phase boundaries

## Reusable knowledge

- The canonical Karpathy rule body now lives in `memories/0_apex/KARPATHY_TIER0_PRINCIPLES.md`, while startup/routing/governance files only mirror the short contract needed for enforcement [Task 1][Task 2]
- `GROUND_KERNEL.md` and `CODEX_DYNAMIC_ROUTING.md` were updated so the Tier-0 map now includes both `GROUND_KERNEL.md` and `KARPATHY_TIER0_PRINCIPLES.md`, keeping the Karpathy layer visible at startup [Task 1]
- Current file state in `0_apex/GROUND_KERNEL.md` keeps the claude-skill lock but now names `skills/claude-app` instead of `skills/claude-frontend`, and records that the rename happened on 2026-05-21 under explicit user authorization
- The required four checks are `Assumptions surfaced`, `Simplicity preserved`, `Surgical scope respected`, and `Verification evidence included`; each check uses `pass | fail | n/a`, and the current file state in `0_apex/KARPATHY_TIER0_PRINCIPLES.md` says this review stays internal by default unless the user asks to see it [Task 2]
- Failure handling is part of the contract: if any compliance check is `fail`, self-correct before finalizing or explicitly declare an unresolved blocker [Task 2]
- Current file state in `2_governance/DRIFT_GUARD_PROTOCOL.md` adds an Anchor rule for long tasks: re-read the original request every 3-5 tool batches or at each phase boundary, classify `on-track` / `minor-drift` / `major-drift`, and fall back immediately if scope has expanded beyond the ask

## Failures and how to do differently

- Symptom: generated routing suddenly contains `memories/.git/*` noise. Cause: nested `.git` trees were not excluded from ignore/router config. Fix: add `.git` exclusions to `.codexignore`, `.openaiignore`, `.claudeignore`, and `codex-router/router-config.json`, then regenerate routing again [Task 1]
- Symptom: final-output guidance drifts between visible-footer and internal-review language. Cause: the rollout captured an `Always Full` preference, but the live Tier-0 file later refined the contract to an internal hidden-by-default review. Fix: re-check `0_apex/KARPATHY_TIER0_PRINCIPLES.md` before mirroring the rule, and only surface the review when the user explicitly asks for it or an unresolved blocker must be declared [Task 2]
- Symptom: a long task starts solving adjacent work that the user did not ask for. Cause: the anchor was not re-read after several tool batches or before a scope-expanding step. Fix: apply the `DRIFT_GUARD_PROTOCOL.md` checkpoint cadence and revert to the last on-track state before continuing

# Task Group: Angel Interior workspace docs, database contract, admin alignment, and local publish/runtime checks
scope: Reuse when the task touches `C:\Users\user\Desktop\angel-interior`, especially root handoff docs, the Angel Supabase contract, active admin cleanup, upload-ignore hygiene, Windows-safe local dev launch, or local-Supabase-to-public publish checks; not a generic Supabase recipe for unrelated projects.
applies_to: cwd=\\?\C:\Users\user\Desktop\angel-interior; reuse_rule=safe for this Angel workspace if you re-check current folder authority, local Docker Supabase state, and which admin panel is active before reusing rollout-specific guidance

## Task 1: Create shared root docs and project authority guidance, success

### rollout_summary_files

- rollout_summaries/2026-05-18T05-58-58-KXJ1-angel_interior_docs_db_cleanup_login_ignore_and_dev_run.md (cwd=\\?\C:\Users\user\Desktop\angel-interior, rollout_path=C:\Users\user\.codex\sessions\2026\05\18\rollout-2026-05-18T13-58-58-019e39aa-8bb7-7031-8ec6-6aa1b8bdce73.jsonl, updated_at=2026-05-18T11:00:06+00:00, thread_id=019e39aa-8bb7-7031-8ec6-6aa1b8bdce73, created root handoff docs and clarified folder roles)

### keywords

- angel-interior, AI_COLLAB_PROJECT_OS.md, MASTER_PLAN.md, DATABASE.md, TABLE_STRUCTURE.md, DATABASE_MARKMAP.md, CROSSWALK.md, root docs, project authority, website-angel-interior, admin-panel-angel, admin-panel-trash

## Task 2: DB recovery, admin cleanup, gitignore, and initial dev launch, success

### rollout_summary_files

- rollout_summaries/2026-05-18T05-58-58-KXJ1-angel_interior_docs_db_cleanup_login_ignore_and_dev_run.md (cwd=\\?\C:\Users\user\Desktop\angel-interior, rollout_path=C:\Users\user\.codex\sessions\2026\05\18\rollout-2026-05-18T13-58-58-019e39aa-8bb7-7031-8ec6-6aa1b8bdce73.jsonl, updated_at=2026-05-18T11:00:06+00:00, thread_id=019e39aa-8bb7-7031-8ec6-6aa1b8bdce73, recovered the missing auth/RBAC/schema layers, cleaned active admin routes, finalized upload-ignore hygiene, and confirmed Windows-safe dev launch)

### keywords

- Supabase, Vben, angel.users, angel.permissions, angel.attachments, auth.users, public.user, create_user, authorize, get_permission_scope, localhost:54323, pnpm.cmd, dev:local, localhost:6006, cloudflared, dist.zip, VITE_SUPABASE_URL

## Task 3: Start `dev:local` for `admin-panel-angel/apps/web-antd` and confirm the real Vite listener, partial

### rollout_summary_files

- rollout_summaries/2026-05-20T09-58-29-xDsO-angel_admin_web_antd_dev_local_startup.md (cwd=\\?\C:\Users\user\Desktop\angel-interior, rollout_path=C:\Users\user\.codex\sessions\2026\05\20\rollout-2026-05-20T17-58-29-019e44d2-8c49-7180-9020-cc0838d8568e.jsonl, updated_at=2026-05-20T10:01:56+00:00, thread_id=019e44d2-8c49-7180-9020-cc0838d8568e, captured the sandbox failure and the later verified Vite listener on localhost:6006)

### keywords

- admin-panel-angel, apps/web-antd, pnpm.cmd, dev:local, Vite, development.localhost, vite.config.mts, Access is denied, sandbox, localhost:6006, node.exe

## User preferences

- when the user asked for root `.md` docs "so that next time ai could easily understand what i do here without research again", default to durable root documentation rather than only chat memory [Task 1]
- when building a content module with a video field, never hardcode `YouTube` in labels - use generic `Video URL` because the user posts TikTok and other sources [Task 2]
- when working in a Vben admin panel with no real notification backend yet, disable mock bell with `widget.notification: false` in `@core/preferences` [Task 2]
- when the user says `admin-panel-angel pnpm run dev:local this`, treat it as a direct run request, not a planning prompt [Task 3]
- when the active file already points at `admin-panel-angel/apps/web-antd/.env.development.localhost`, check the matching app directory before launching [Task 3]

## Reusable knowledge

- Durable root stack: `AI_COLLAB_PROJECT_OS.md` (authority), `MASTER_PLAN.md` (phases), `DATABASE.md` (canonical schema/auth/RLS), `TABLE_STRUCTURE.md` (quick inventory), `DATABASE_MARKMAP.md` (visual mindmap), `CROSSWALK.md` (doc alignment)
- Active target: `admin-panel-angel`; reference-only: `admin-panel-trash`. Angel schema key: `schema=angel`, `project id=b3e45339-0de0-4073-b03a-7f5468bffe77`, storage bucket `angel-interior`
- Login is a three-layer binding: `auth.users` + `public.user` + `angel.users`; missing any layer breaks login/profile/admin
- Windows launch: `pnpm.cmd run dev:local` from `admin-panel-angel/apps/web-antd`; confirmed listener `http://localhost:6006/`
- Current file state in `2_governance/VBEN_ADMIN_LOCAL_DEV_PROTOCOL.md` prefers `pnpm.cmd run dev:local` from the panel root, lets root `dev:local` filter to `@vben/web-antd`, and says to wait for the `VITE ... ready` line before curling `http://localhost:6006/`
- Cloudflare publish flow: verify local auth+rest -> create tunnel -> proxy `127.0.0.1:54321` -> `cloudflared service install` (elevated PS) -> `pnpm.cmd build:antd` -> upload dist.zip -> hard-refresh
- Related skills: `skills/vben-local-supabase-preflight/SKILL.md`, `skills/vben-local-supabase-cloudflare-publish/SKILL.md`

## Failures and how to do differently

- Schema looks present but login fails -> content tables only, missing auth bridge/RBAC/helper functions. Fix: verify table + function inventory together
- `INSERT` still 403 after RLS policy -> missing paired `permissions` row. Fix: treat RLS + permissions as dual-grant checklist
- Storage files 404 -> path starts with `/`. Fix: normalize paths to omit leading slash before `getStorageUrl()`
- Public DB hostname returns 502 -> `rest` service is down. Fix: run `supabase status`, check both `/auth/v1/health` and `/rest/v1/` before redeploying
- `pnpm run dev:local` fails with `Cannot read directory "../../../../.." : Access is denied.` or cannot resolve `vite.config.mts` -> sandboxed Vite/esbuild workspace resolution is blocked. Fix: retry outside the sandbox, then verify the owning process is the app's `node.exe` / Vite listener before reporting `localhost:6006`

# Task Group: Codex home migration, ignore standardization, and runtime policy
scope: Reuse when the task touches the user's `C:\Users\user\.codex` home, especially migration away from `.gemini`, cross-tool ignore hygiene, core-safe skill restoration, or low-token runtime behavior; not a generic repo-maintenance guide.
applies_to: cwd=\\?\C:\Users\user\.codex; reuse_rule=safe for this user's Codex-home workspace if you re-check live routing files, current skill inventory, and whether cleanup targets are active runtime files

## Task 1-5: Cross-tool ignores, skill baseline, .gemini migration, root audit, perf benchmark (all partial/success)

### rollout_summary_files

- rollout_summaries/2026-05-13T06-35-46-ELIk-codex_migration_optimization_and_cross_tool_ignore.md (cwd=\\?\C:\Users\user\.codex, updated_at=2026-05-13T08:54:23+00:00)

### keywords

- .claudeignore, .geminiignore, .openaiignore, .codexignore, plan-first, low reasoning, config.toml, model_reasoning_effort, AGENTS.md, libraries/codex-migrated, skills/.system, skill-installer, Lean Fast Lane, Deep Capability Lane, 00_CODEX_PERF_BENCHMARK.md

## User preferences

- when the user wants ignore files aligned, standardize `.claudeignore`, `.geminiignore`, `.openaiignore` together with `.codexignore`
- when the user asks for "plan mode always trigger on", default to plan-first + concise with deeper work only for complex/risky tasks
- when the user asks to remove old/useless root files, do root-by-root impact analysis first; only delete low-risk items directly

## Reusable knowledge

- `config.toml`: `gpt-5.3-codex` + `model_reasoning_effort = "low"`; runtime docs now express plan-first + deferred heavy reads
- Minimum safe skill baseline: `skills/.system/.codex-system-skills.marker`, `skill-installer`, `skill-creator`, `plugin-creator`, `openai-docs`, `imagegen`
- `libraries/codex-migrated` is the live migration target; stale `gemini-migrated` strings in `REMOVED:` history do not mean live routing is broken
- Current file state in `2_governance/artifacts/skill_path_router.md` is now a canonical trigger-to-entrypoint index; `ai claude app` routes to `skills/claude-app/WORKING_PROGRESS.md`, and future skill routing work should use that map before scanning skill directories
- Current file state in `2_governance/ARCHITECTURE_COMPARISON.md` treats `claude-app` as the mobile / PWA Vue 3 + Supabase + Capacitor builder; do not reuse older `claude-frontend` wording for current Codex-home skill routing
- `0_apex/GROUND_KERNEL.md` classifies both Tier-0 files plus `codex-router/codex-manifest.json` as `tier_0_nuclear` - require explicit user confirmation before edit/delete
- Do not touch `logs_2.sqlite`, `state_5.sqlite`, or their `-wal`/`-shm` files while Codex is running
- `00_CODEX_PERF_BENCHMARK.md` stores benchmark scaffold for routine/medium/deep comparisons
- Current file state in `2_governance/KNOWLEDGE_ROT_PROTOCOL.md` caps `MEMORY.md` at 300 lines and trims the oldest task groups from the bottom while preserving the governance comment plus top profile/preferences during rot-audit

## Failures and how to do differently

- Ignore standardization only updates `.codexignore` -> tools diverge. Fix: update all four ignore files together from the same baseline
- Migrated routing still shows `gemini-migrated` -> stale generated `REMOVED:` history, not a live bug. Fix: distinguish live path bugs from stale generated history before acting
- Symptom: a Codex-home skill or router update still points at `claude-frontend`. Cause: stale pre-2026-05-21 naming was copied forward from older `.gemini` or historical notes. Fix: for live `.codex` routing, replace it with `claude-app`; only keep `claude-frontend` when you are intentionally referring to old `.gemini` paths or historical rollout evidence
