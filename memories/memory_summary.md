v1

## User Profile
The user uses Codex as a practical Windows/PowerShell partner across local repos, Supabase-backed app/admin work, website edits, and Codex memory maintenance. They want route-first context loading when they ask for `.codex` knowledge, docs/status-first orientation when entering an unfamiliar workspace, and evidence-backed fixes that follow the real repo/schema/config path instead of speculative workarounds. They are especially sensitive to destructive changes: live content should stay intact, VPS/schema operations should be narrowly scoped, and local environments should be made truly migration-ready rather than only diagnosed. They also like durable outputs that help the next agent move faster, such as AI-oriented `README.md` files and consolidated memory updates.

## User preferences
- When the user says `ai read .codex knowledge`, use route-first selective loading from the boot router/indexes instead of broad recursion.
- When the user asks to understand a project or tooling folder, start with root docs/status docs first and, if useful, leave behind an AI-oriented `README.md` with workflow/status context.
- If the user asks for schema/data to be "very accurate", "really fit", or "complete", fix the real registry/config/schema path instead of offering a workaround or UI-only change.
- In fragile live-content or VPS work, preserve current content/data by default and scope edits narrowly until the exact route, loader, or schema boundary is verified.
- For VPS schema pushes, default to schema-scoped, import-only, non-destructive behavior unless the user explicitly asks to overwrite/replace.
- After sync/update/run requests, continue into the obvious verification step (`npm.cmd run build`, listener ownership check, backup rerun) without waiting for another prompt.
- On this Windows PowerShell setup, prefer `npm.cmd` / `pnpm.cmd` when bare `npm` / `pnpm` may hit execution-policy issues.
- In full-access sessions without approval/review gates, avoid repetitive step-end prompts like `Step X done - confirm or adjust?`; continue through obvious next steps and only pause for real decisions, hidden risk, destructive actions, or ambiguous tradeoffs. [ad-hoc note]
- If the user asks for a comparison table, include Before, After, Token cost, Speed, Speed increase %, and Rating.

## General Tips
- Verify the real repo root before running Git commands; parent workspace folders have caused false assumptions in multiple repos.
- For `.gemini` / `.codex` knowledge reads on this machine, indexes and routing docs beat broad tree scans; use PowerShell inventory when `rg` hits Windows access issues.
- For local Angel Supabase backup work, do not assume schema name, bucket id, and policy prefix match; `angelinterior`, `angel-interior`, and `angel_interior` are distinct.
- For backup warnings, separate true local gaps from script lookup bugs by checking the live DB/config/container state before declaring something missing.
- If a batch workflow "stops halfway", inspect nested child scripts for blocking `pause` prompts before redesigning the flow.
- For local dev/build verification, do not trust a port alone; confirm the owning `node.exe` / Vite command or the actual build output.

## What's in Memory

### C:\Users\user\Documents\restore-local

#### 2026-05-28

- restore-local backup/restore toolkit and AI README: restore-local, README.md, backup-local.bat, restore-local.bat, restore-single.bat, manifest.json, trash-20260522-140801
  - desc: Search this first when the user wants the `restore-local` folder explained, mapped, or documented for future AI use; applies to `cwd=C:\Users\user\Documents\restore-local`.
  - learnings: `restore-local` is an operations workspace, `README.md` is the orientation file, and the live packaged snapshot is under `restore-single\trash-20260522-140801\trash-20260522-140801`.
- Safe VPS schema push and cleanup guardrails: reset & restore-supabase.bat, option 3, import-only, NO_PAUSE=1, angelInterior, angelinterior, table_schema, pg_toast
  - desc: Search this first when the user wants to push one local schema to VPS or safely inspect/delete duplicate schemas without touching unrelated data; applies to `cwd=C:\Users\user\Documents\restore-local`.
  - learnings: option 3 should stay import-only by default, child-script `pause` caused the mid-flow stop, and duplicate-schema cleanup requires exact casing plus dependency checks.

### C:\Users\user\Documents\supabase-project-backup-restore

#### 2026-05-28

- Angel local Supabase migration-readiness and backup repair: supabase-project-backup-restore, angelinterior, public.project, local-backup.bat, scripts/01-backup-local.sh, config.toml, angel-interior, angel_interior
  - desc: Search this first when the user wants the local Angel Supabase stack made VPS-ready or when backup warnings mention schema/storage/policy mismatches; applies to `cwd=C:\Users\user\Documents\supabase-project-backup-restore` plus shared `C:\Users\user\Documents\local-supabase`.
  - learnings: `public.project.schema_name` drives backup resolution, the three Angel names differ, and `local-backups/angelinterior-20260528-182503` is the best verified migration-grade backup.

### C:\Users\user\Desktop\angel-interior

#### 2026-05-28

- SketchUp paid checkout placeholder flow: website-angel-interior, /checkout/sketchup/, /sketchup-free-resources, sketchup-free-resources.php, Stripe payment comming soon, 5 sec timer
  - desc: Search this first when paid SketchUp resources need a temporary checkout stage without disturbing live resource content; applies to `cwd=C:\Users\user\Desktop\angel-interior`.
  - learnings: the user wants a staged placeholder flow, not a finalized Stripe rollout, and is especially sensitive to live content/data loss around this route split.

### C:\Users\user\Desktop\zenius

#### 2026-05-26

- Repo sync with stash/pull/pop and build verification: zenius-tech-2026, git stash push -m "before pull", git pull origin main, git stash pop, src/style.css, npm.cmd run build
  - desc: Search this first when local edits block `git pull` in the real Zenius repo and the goal is to preserve work, resolve conflicts, and end with a verified clean build; applies to `cwd=C:\Users\user\Desktop\zenius\zenius-tech-2026`.
  - learnings: the real repo is `zenius-tech-2026`, `git stash pop` can leave CSS conflicts, and `npm.cmd run build` was the reliable finish-line check.

#### 2026-05-22

- Zone 1/2/3 tag design update in `template/`: template, zone tag, HomeView.vue, StandingsView.vue, zone-tag-rail, zone-tag, style.css
  - desc: Search this first for presentation-only selector redesigns in `template/`, especially when Home and Standings must stay visually aligned; applies to `cwd=C:\Users\user\Desktop\zenius\template`.
  - learnings: this workspace treats `template/` as the editable redesign target, and shared selector styling belongs in `style.css` with `npm.cmd run build` verification.

### C:\Users\user\Desktop\trash-container-app

#### 2026-05-26

- Docs-first schema audit and map/data cleanup: trash-container-app, STATUS.md, DATABASE.md, web-admin-app, admin-panel-trash, MapView.vue, bin_sizes, latitude, longitude
  - desc: Search this first when the user wants the trash apps aligned to the real Supabase `trash` schema, especially for dummy-vs-live audits, coordinate flows, and desktop order/map UX; applies to `cwd=C:\Users\user\Desktop\trash-container-app`.
  - learnings: `STATUS.md` is the live state doc, `task.order.binSize` is the correct map filter axis, and desktop admin already passes coordinate fields through `create_order_with_tasks`.

### Older Memory Topics

#### C:\Users\user\Desktop\angel-interior

- `admin-panel-angel` `dev:local` startup and listener verification: admin-panel-angel, apps/web-antd, pnpm.cmd, dev:local, localhost:6006, vite.config.mts
  - desc: Use this for terse local-run requests or Vite listener verification in the Angel admin app; applies to `cwd=C:\Users\user\Desktop\angel-interior\admin-panel-angel\apps\web-antd`.
