thread_id: 019e39aa-8bb7-7031-8ec6-6aa1b8bdce73
updated_at: 2026-05-18T11:00:06+00:00
rollout_path: C:\Users\user\.codex\sessions\2026\05\18\rollout-2026-05-18T13-58-58-019e39aa-8bb7-7031-8ec6-6aa1b8bdce73.jsonl
cwd: \\?\C:\Users\user\Desktop\angel-interior

# Angel Interior workspace was turned into a durable multi-doc operating system, the Angel Supabase schema was brought online with missing auth/permission/attachment layers, the active admin panel was cleaned down to Angel-safe modules, and the login/ignore/dev-flow were aligned for localhost use.

Rollout context: The workspace is `C:\Users\user\Desktop\angel-interior` and contains three important projects: `website-angel-interior` (PHP site; business truth), `admin-panel-trash` (active/working Vben + Supabase reference/build base), and `admin-panel-angel` (historical success project, but later explicitly treated as locked read-only reference). The user wanted both Codex and Claude to share the same root docs, then wanted the admin panel to be cleaned and aligned with a new Angel Interior database and local login flow.

## Task 1: Route-first knowledge loading and shared root docs
Outcome: success

Preference signals:
- The user repeatedly asked for a way for “both ai could read .md in root project folder” and to “fast understanding these project routes and path and what they do” -> this indicates they want a shared, root-level operating system for both Codex and Claude instead of repeating context in chat.
- The user said the plan should be “step by step” and “beautifully” organized -> they want phased planning with explicit checkpoints, not ad hoc edits.
- The user later clarified that `admin-panel-angel` is the success/reference project and should be locked from edits -> future sessions should treat historical success projects as read-only unless explicitly unlocked.

Key steps:
- Read the existing root docs and project docs for `admin-panel-trash`, `admin-panel-angel`, and `website-angel-interior`.
- Created root docs to make the workspace understandable without rereading raw chat:
  - `AI_COLLAB_PROJECT_OS.md`
  - `MASTER_PLAN.md`
  - `DATABASE.md`
- Established a cross-AI workflow: root docs are the first read, `DATABASE.md` is the schema contract, and `MASTER_PLAN.md` is the execution tracker.

Failures and how to do differently:
- The first version of the docs was too generic and not strict enough about project authority boundaries. It was later rewritten to clearly separate active build target, reference-only history, and business source-of-truth.
- A project note mixing reusable and Angel-specific guidance turned out to be too narrow for future Claude-style reuse; it was later split into reusable and project-specific memory notes.

Reusable knowledge:
- `website-angel-interior/BLUEPRINT.md` and `CLAUDE.md` define the PHP site as a route/template-based marketing site with hardcoded data and no live DB.
- `admin-panel-trash` is the editable Vben/Supabase working base.
- `admin-panel-angel` is the historical reference and later should be treated as locked read-only unless explicitly unlocked.
- A root doc stack is useful here: one file for collaboration OS/rules, one for execution phases, one for database contract.

References:
- [1] Root docs created: `AI_COLLAB_PROJECT_OS.md`, `MASTER_PLAN.md`, `DATABASE.md`.
- [2] `website-angel-interior/CLAUDE.md` says it is a PHP site with no database and no jQuery.
- [3] `admin-panel-trash/README.md`, `DOCS.md`, `SUPABASE.md`, `TRASH_PROJECT_BLUEPRINT.md` establish the trash/vben/supabase model.
- [4] `admin-panel-angel/CLAUDE.md` and route/store files show the Angel panel’s current Vben structure.

## Task 2: Angel Supabase database contract and missing-table recovery
Outcome: success

Preference signals:
- The user said the mission is to “construct a brand new database from website-angel-interior” and use `DATABASE.md` as the direct source of truth -> future DB work should update the database contract first, then migrations.
- The user explicitly asked that `users`, `permissions`, and `attachments` “with all authorization needed, rules needed” must not be missed -> these are must-check core tables, not optional extras.
- The user wanted “step by step” and later asked for the missing layers to be saved into `.codex` knowledge/skills -> future schema planning should always include auth bridge, RBAC, and attachment/storage rules.

Key steps:
- Read the Angel migration set and discovered the new Angel schema was missing key layers the UI expected.
- Patched and added missing schema support for the Angel project:
  - shared camelCase trigger helper
  - `angel.users`
  - `angel.permissions`
  - `angel.attachments`
  - attachment permission seeds and safe-delete RPC
- Updated the root docs and the quick-view mirrors to keep them aligned:
  - `DATABASE.md`
  - `TABLE_STRUCTURE.md`
  - `DATABASE_MARKMAP.md`
  - `CROSSWALK.md`
- Applied the missing Angel migrations into the local Docker Supabase database and verified the schema.

Failures and how to do differently:
- A shared trigger function originally only handled snake_case `updated_at`; Angel business tables used camelCase `updatedAt`, which would have broken updates. A separate camelCase trigger helper fixed this.
- Initial verification showed the schema existed but the row-count query was malformed once; rerunning with a safer heredoc-style query worked.
- There was a mismatch between old Trash-era code assumptions and the new Angel Step 1 schema; the correct fix was to add the missing Angel core tables rather than pretending the old Trash tables were still the target.

Reusable knowledge:
- The Angel project now uses `public.project` + `public.role` + `public.permission` + `public.role_permission` + `public.user` plus schema-local `angel.users`, `angel.permissions`, and `angel.attachments`.
- Local Docker Supabase verification succeeded with `http://localhost:54323`.
- The applied migrations created/verified these Angel schema tables: `attachments`, `blog_categories`, `blog_posts`, `contact_submissions`, `material_categories`, `material_resources`, `media_assets`, `permissions`, `sketchup_categories`, `sketchup_resources`, `users`.
- Verified Angel functions now include `create_user`, `update_user`, `delete_user`, `restore_user`, `safe_delete_active_attachment`, `authorize`, `get_permission_scope`.

References:
- [1] Applied migrations: `027_angel_schema_core.sql`, `029_angel_permissions_seed.sql`, `033_angel_users_business_table_rpc.sql`, `034_angel_permissions_business_table.sql`, `035_angel_attachments_business_table.sql`.
- [2] Verification: `angel.permissions = 144`, `angel.users = 0`, `angel.attachments = 0` after migration application.
- [3] Local DB rows showed `admin@interiordesignangel.com` in `auth.users`, `public.user`, and `angel.users`.
- [4] `admin-panel-angel/apps/web-antd/src/sql/README.md` was updated to include the attachments table/migration.

## Task 3: Active Angel admin cleanup, login, and module alignment
Outcome: success

Preference signals:
- The user said `admin-panel-angel` is a “history successed project” but also later said it should be cleaned as the active Angel admin panel -> future changes should keep historical logic out of the active route surface unless it is still needed.
- The user explicitly asked to “clean the modules inside my admin panel” and to follow the Claude/Codex step-by-step skills for that cleanup -> route/menu/store cleanup should be done methodically, starting from entry points.
- The user wanted the localhost login email changed from Trash branding to Angel branding -> login defaults should track the current Angel identity, not old project branding.

Key steps:
- Reduced the active route surface in `admin-panel-angel` by removing Trash-era route modules and keeping only Angel-safe active modules.
- Adjusted `admin-panel-angel/apps/web-antd/src/router/routes/modules/nationals.ts` so the master-data route now redirects to attachments rather than the old bins/bin-sizes path.
- Removed stale route files for old Trash modules: customers, customer-transactions, drivers, driver-tasks, orders, workflow-test.
- Updated auth role mapping in `supabase-auth.ts` so it uses Angel roles only (`super_admin`, `admin`, `editor`, `staff`, `viewer`) instead of the old `driver` mapping.
- Neutralized a stale `fetchDriverOptions()` helper in `stores/users.ts` so it no longer depends on the old driver role.
- Updated the login page autofill from `superadmin@trash.com` to `admin@interiordesignangel.com`.
- Confirmed the local Docker Supabase account already matched the requested email/role layers:
  - `auth.users.email = admin@interiordesignangel.com`
  - `public.user.email = admin@interiordesignangel.com`
  - `angel.users.email = admin@interiordesignangel.com`
  - `angel.users.role = admin`

Failures and how to do differently:
- A full `pnpm typecheck` could not run because dependencies were missing in the checkout (`vue-tsc` not installed locally).
- The cleanup was intentionally done at the active route/menu surface first; old stores/views/types still exist in the repo and may need a later purge if the user wants a stricter cleanup.
- The dev-only workflow-test panel still exists in `app.vue`, though its route was removed; that is a lower-priority leftover.

Reusable knowledge:
- For this codebase, the active route entry files are the safest place to disable old modules quickly.
- The active Angel shell can be reduced to `users` and `attachments` first, then expanded later.
- Login defaults and role-code mappings need to match the actual Angel project roles or the localhost UX will keep showing Trash-era identities.

References:
- [1] Active route modules after cleanup: only `nationals.ts` and `users.ts` remained.
- [2] Removed route files: `customers.ts`, `customer-transactions.ts`, `drivers.ts`, `driver-tasks.ts`, `orders.ts`, `workflow-test.ts`.
- [3] Updated login autofill file: `admin-panel-angel/apps/web-antd/src/views/_core/authentication/login.vue`.
- [4] `admin-panel-angel/apps/web-antd/src/api/core/supabase-auth.ts` role mapping was changed away from `driver`.

## Task 4: Ignore-file finalization and GitHub upload readiness
Outcome: success

Preference signals:
- The user asked what should be ignored before GitHub upload and confirmed they want to keep shared env files visible/trackable while ignoring local noise -> future `.gitignore` changes should preserve shared mode env files and only exclude local/private/generated artifacts.
- The user specifically approved “Keep shared envs (Recommended)” -> do not blanket-ignore all `.env*` files in this repo.

Key steps:
- Inspected `admin-panel-angel/.gitignore` against the actual repository tree.
- Added local-noise exclusions:
  - `test-results/`
  - `.mcp.json`
- Verified with `git status --ignored --short` that the added entries are ignored while shared env files remain visible.

Failures and how to do differently:
- `admin-panel-angel` contains many committed `.env` mode files by design, so it would have been wrong to ignore every `.env*` file.
- This repo also contains a lot of untracked content overall, which is separate from ignore policy; `.gitignore` only handles generated/noisy paths, not repo-wide uncommitted state.

Reusable knowledge:
- For this project, shared `.env`, `.env.development`, `.env.production`, etc. are intentionally part of the repo strategy.
- Local/private overrides should stay in `.env.local` / `.env.*.local`.
- `test-results/` and `.mcp.json` are good candidates for ignore when preparing for GitHub upload.

References:
- [1] Updated ignore file: `admin-panel-angel/.gitignore`.
- [2] Verification output showed `!! .mcp.json` and `!! test-results/` under ignored paths.
- [3] Shared env files remained trackable in the tree (`.env`, `.env.development`, `.env.production`, etc.).

## Task 5: Local dev server launch
Outcome: partial

Preference signals:
- The user directly requested `pnpm dev` / `pnmp run dev` / `pnpm dev:local` for the Angel admin panel -> future sessions should use the workspace’s Windows-safe `pnpm.cmd` path when PowerShell blocks scripts.

Key steps:
- Launched the Angel admin dev server from `admin-panel-angel/apps/web-antd` using `pnpm.cmd run dev:vps` and then `pnpm.cmd run dev:local`.
- Confirmed a `node` process remained running after launch.

Failures and how to do differently:
- The environment could not reliably expose the exact Vite listening port, so the dev launch was only partially verified.
- A full TypeScript check also failed because local dependencies were missing (`vue-tsc` not recognized).
- If this becomes a recurring need, next time verify the app has dependencies installed before launching dev, and use port checks or log capture from the process output if available.

Reusable knowledge:
- In this workspace, PowerShell policy may block `pnpm`; `pnpm.cmd` is the safer launch path.
- `admin-panel-angel/apps/web-antd` is the right working directory for the frontend dev server.
- A live `node` process after launch is a weak but useful signal that the dev command started.

References:
- [1] Launch commands used: `pnpm.cmd run dev:vps`, then `pnpm.cmd run dev:local`.
- [2] A `node` process with the launch start time remained running.
- [3] Port detection was inconclusive from this environment.
