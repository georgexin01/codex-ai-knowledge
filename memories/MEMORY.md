<!-- AI GOVERNANCE: MAX 300 LINES. When adding new task groups, trim oldest from bottom. Auto-trim fires on rot-audit when line count exceeds 300. -->

# Task Group: restore-local Supabase backup/restore workflow and safe VPS schema operations
scope: Reuse when the user is working in `restore-local` to understand the backup/restore toolkit, document it for future AI use, harden VPS push safety, or inspect schema-only cleanup paths; not a generic Supabase guide for unrelated repos.
applies_to: cwd=\\?\C:\Users\user\Documents\restore-local; reuse_rule=safe for this operations folder while the main batch scripts (`backup-local.bat`, `restore-local.bat`, `restore-single.bat`, `reset & restore-supabase.bat`) remain the restore/sync entrypoints

## Task 1: Map `restore-local` and write an AI-oriented root README, success

### rollout_summary_files

- rollout_summaries/2026-05-28T09-17-33-enR7-restore_local_supabase_safe_import_and_schema_deletion_guida.md (cwd=\\?\C:\Users\user\Documents\restore-local, rollout_path=C:\Users\user\.codex\sessions\2026\05\28\rollout-2026-05-28T17-17-33-019e6ddf-f0df-7311-9f73-b76444e6e4a9.jsonl, updated_at=2026-05-28T09:52:30+00:00, thread_id=019e6ddf-f0df-7311-9f73-b76444e6e4a9, fresher restatement of the folder map and README outcome)
- rollout_summaries/2026-05-28T09-10-01-IND5-restore_local_readme_supabase_backup_restore_guide.md (cwd=\\?\C:\Users\user\Documents\restore-local, rollout_path=C:\Users\user\.codex\sessions\2026\05\28\rollout-2026-05-28T17-10-01-019e6dd9-0d7a-7281-ad36-a6163c86d01b.jsonl, updated_at=2026-05-28T09:13:18+00:00, thread_id=019e6dd9-0d7a-7281-ad36-a6163c86d01b, original README/documentation pass)

### keywords

- restore-local, README.md, backup-local.bat, restore-local.bat, restore-single.bat, restore-trash.bat, reset & restore-supabase.bat, manifest.json, trash-20260522-140801, p%, vps comand.txt

## Task 2: Harden `reset & restore-supabase.bat` option 3 for safe local-to-VPS schema push, partial

### rollout_summary_files

- rollout_summaries/2026-05-28T09-17-33-enR7-restore_local_supabase_safe_import_and_schema_deletion_guida.md (cwd=\\?\C:\Users\user\Documents\restore-local, rollout_path=C:\Users\user\.codex\sessions\2026\05\28\rollout-2026-05-28T17-17-33-019e6ddf-f0df-7311-9f73-b76444e6e4a9.jsonl, updated_at=2026-05-28T09:52:30+00:00, thread_id=019e6ddf-f0df-7311-9f73-b76444e6e4a9, import-only safe mode and child-script pause fix)

### keywords

- reset & restore-supabase.bat, option 3, local-to-VPS, import-only, SAFE MODE aborted: import-only mode never replaces existing VPS schemas, NO_PAUSE=1, backup-local.bat, Press any key to continue . . ., replace-on-exists

## Task 3: Inspect duplicate VPS schemas and define the safest schema-only cleanup path, uncertain

### rollout_summary_files

- rollout_summaries/2026-05-28T09-17-33-enR7-restore_local_supabase_safe_import_and_schema_deletion_guida.md (cwd=\\?\C:\Users\user\Documents\restore-local, rollout_path=C:\Users\user\.codex\sessions\2026\05\28\rollout-2026-05-28T17-17-33-019e6ddf-f0df-7311-9f73-b76444e6e4a9.jsonl, updated_at=2026-05-28T09:52:30+00:00, thread_id=019e6ddf-f0df-7311-9f73-b76444e6e4a9, duplicate-schema inspection without executing destructive cleanup)

### keywords

- angelInterior, angelinterior, quoted schema names, table_schema, information_schema.tables, pg_toast, drop schema ... cascade, b3e45339-0de0-4073-b03a-7f5468bffe77, schema-only cleanup

## User preferences

- when the user said `ai read .codex knowledge first then do above request in chat`, load the `.codex` routing/knowledge layer first when they explicitly ask for it before working inside the project folder [Task 1]
- when the user asked to "study this folder", explain the flow "step by step", and save it in `readme.md` so future AI can "quickly understanding this restore-local folder", produce an AI-oriented root README with workflow/status context instead of only a chat summary [Task 1]
- when the user said option 3 should "only restore 1 schema from local into vps" and "will not touch a single content in vps", default VPS schema pushes to schema-scoped, non-destructive behavior with no collateral changes [Task 2]
- when the user said `will not overwrite or remove or delete a single schema in vps or any tables in vps cause it was cratical problem if it happen` and later asked to "just import from locap to vps in step 3", treat replace/delete behavior as a critical-risk path and keep import-only abort-on-existing-schema as the default unless the user explicitly reopens overwrite behavior [Task 2]
- when the user emphasized `do not alter any other project schema.. not touch no edit no changes no update`, prefer the narrowest schema-only inspection/deletion path and make exact schema casing and dependency checks explicit before suggesting destructive SQL [Task 3]

## Reusable knowledge

- `restore-local` is an operations workspace, not an app source repo; the root scripts are the workflow map, and `README.md` now serves as the AI-oriented orientation file for backup, full restore, single-project restore, trash-only restore, and VPS sync flows [Task 1]
- `backup-local.bat` creates timestamped backups under `C:\Users\user\Documents\supabase-backup-restore` and captures SQL dumps, auth data, storage metadata, grants, zipped storage files, zipped edge functions, and `.env` [Task 1]
- `restore-local.bat` is the destructive full local restore path; `restore-single.bat` is the safer packaged single-project restore path driven by `manifest.json`; `reset & restore-supabase.bat` is the VPS sync controller for full restore, pull-one-schema, and push-one-schema modes [Task 1]
- The packaged snapshot currently present is `restore-single\trash-20260522-140801\trash-20260522-140801`, with `schema: trash`, `projectId: fddcc8d4-2f70-4cdc-b5a4-b2fee7b9d8f6`, SQL parts `01-schema.sql` through `08-public-functions.sql`, plus `edge-functions/` and `storage-files/` [Task 1]
- `p%` is sensitive scratch material and should stay out of future docs/summaries; the root `supabase/` folder is only lightweight metadata, not the full app tree [Task 1]
- Option 3 in `reset & restore-supabase.bat` now uses `NO_PAUSE=1` to call `backup-local.bat` without blocking, validates the extracted SQL, checks whether the schema already exists on VPS, and aborts if it does [Task 2]
- The user-preferred VPS push default here is: import a new schema only; do not replace an existing same-name schema on VPS [Task 2]
- PostgreSQL treats `angelInterior` and `angelinterior` as distinct quoted schema names; in the inspected VPS state both existed, each with the same 9 business tables, and no matching `public.project` or storage bucket row was found for `b3e45339-0de0-4073-b03a-7f5468bffe77` [Task 3]

## Failures and how to do differently

- `restore-trash.bat` appeared path-stale because it pointed outside the real packaged snapshot location -> verify the actual `restore-single\...` folder before trusting shortcut scripts [Task 1]
- The scripts use inconsistent hardcoded base paths (`install-supabase\supabase\docker` vs `local-supabase\supabase`) -> check and normalize machine-specific paths before execution instead of assuming portability [Task 1]
- A parent batch file that "stops halfway" may actually be blocked by a child script `pause` -> inspect nested batch calls first and add a bypass flag like `NO_PAUSE=1` before redesigning the workflow [Task 2]
- Replace-on-exists was explored but explicitly rejected by the user -> do not reintroduce overwrite/replace semantics as the default safe path for VPS pushes [Task 2]
- One schema inspection query failed because `information_schema.tables` uses `table_schema`, not `schema_name` -> use the correct column names when verifying duplicate-schema state [Task 3]
- `drop schema ... cascade` is still high risk even in a schema-only cleanup task -> stop unless dependency checks are explicit and anything outside `pg_toast` has been ruled out [Task 3]

# Task Group: Angel local Supabase migration-readiness and backup repair
scope: Reuse when the user wants the local Angel Interior Supabase stack audited and made VPS-migration ready, especially schema-name mismatches, storage naming mismatches, backup fidelity, and local completeness checks; not a generic Supabase guide for unrelated projects.
applies_to: cwd=\\?\C:\Users\user\Documents\supabase-project-backup-restore and C:\Users\user\Documents\local-supabase; reuse_rule=safe for this Angel/local-supabase environment if `angelinterior` remains the real schema and `scripts/01-backup-local.sh` plus `local-backup.bat` remain the backup path

## Task 1: Fix `angelinterior` schema-name mismatch in local backup tooling, success

### rollout_summary_files

- rollout_summaries/2026-05-28T10-11-02-xAs7-angelinterior_local_supabase_backup_storage_policy_fix.md (cwd=\\?\C:\Users\user\Documents\supabase-project-backup-restore, rollout_path=C:\Users\user\.codex\sessions\2026\05\28\rollout-2026-05-28T18-11-10-019e6e10-e86a-73a1-9ba8-2119cccef3d7.jsonl, updated_at=2026-05-28T10:25:39+00:00, thread_id=019e6e10-e86a-73a1-9ba8-2119cccef3d7, corrected registry schema and revalidated backup resolution)

### keywords

- supabase-project-backup-restore, angelinterior, public.project, schema_name, local-backup.bat, scripts/01-backup-local.sh, pg_dump: error: no matching schemas were found, information_schema.schemata, b3e45339-0de0-4073-b03a-7f5468bffe77

## Task 2: Fix storage bucket/policy detection and capture real storage assets, success

### rollout_summary_files

- rollout_summaries/2026-05-28T10-11-02-xAs7-angelinterior_local_supabase_backup_storage_policy_fix.md (cwd=\\?\C:\Users\user\Documents\supabase-project-backup-restore, rollout_path=C:\Users\user\.codex\sessions\2026\05\28\rollout-2026-05-28T18-11-10-019e6e10-e86a-73a1-9ba8-2119cccef3d7.jsonl, updated_at=2026-05-28T10:25:39+00:00, thread_id=019e6e10-e86a-73a1-9ba8-2119cccef3d7, separated schema name from bucket id and policy prefix to eliminate false warnings)

### keywords

- angel-interior, angel_interior, storage.buckets, storage.objects, pg_policies, No physical storage files found for 'angelinterior', No storage policies matching 'angelinterior_*' found, /mnt/stub/stub/angel-interior, local-backups/angelinterior-20260528-182303

## Task 3: Audit local Supabase completeness and improve migration backup fidelity, success

### rollout_summary_files

- rollout_summaries/2026-05-28T10-11-02-xAs7-angelinterior_local_supabase_backup_storage_policy_fix.md (cwd=\\?\C:\Users\user\Documents\supabase-project-backup-restore, rollout_path=C:\Users\user\.codex\sessions\2026\05\28\rollout-2026-05-28T18-11-10-019e6e10-e86a-73a1-9ba8-2119cccef3d7.jsonl, updated_at=2026-05-28T10:25:39+00:00, thread_id=019e6e10-e86a-73a1-9ba8-2119cccef3d7, audited RLS/policies/config and verified a migration-grade backup)

### keywords

- config.toml, api.schemas, public.custom_access_token_hook, RLS, policy count 43, tables 10, local-backups/angelinterior-20260528-182503, local-supabase, VPS migration, complete local settings

## User preferences

- when the backup tool showed `angel` but the user said the schema should be `angelinterior` and asked to "fix this wrong", correct the local registry/tooling to the real schema instead of asking the user to work around it [Task 1]
- when the user said they were moving from local to VPS soon and wanted settings/config/policies "complete", default to migration-readiness work that fixes the local environment and the backup path, not explanation-only guidance [Task 1][Task 2][Task 3]
- when the user asked whether warnings were "all ok or my local is missing those setting? like no policy?", distinguish harmless script warnings from true local gaps with real verification instead of guessing [Task 2]

## Reusable knowledge

- `public.project` is the lookup source for `local-backup.bat`; if its `schema_name` is wrong, the backup prompt is wrong and `pg_dump` can fail with `pg_dump: error: no matching schemas were found` even when the schema exists [Task 1]
- For Angel, three names must be treated independently: DB schema `angelinterior`, storage bucket `angel-interior`, and storage policy prefix `angel_interior` [Task 2]
- The live local storage files were verified under `supabase_storage_local-supabase:/mnt/stub/stub/angel-interior`, and the matching policies were `angel_interior_auth_delete`, `angel_interior_auth_insert`, `angel_interior_auth_update`, and `angel_interior_public_read` [Task 2]
- Shared local Supabase repo: `C:\Users\user\Documents\local-supabase`; its `supabase/config.toml` already exposes `angelinterior` in `api.schemas` and should be copied into backups for VPS migration context [Task 3]
- The local Angel DB was already mostly complete: all 10 `angelinterior` tables had RLS enabled, 43 policies existed, and `public.custom_access_token_hook` matched the config hook reference [Task 3]
- Best verified migration backup was `local-backups/angelinterior-20260528-182503`, which captured schema/data, auth/public rows, storage metadata, physical storage files, storage policies, edge functions, and `config.toml` [Task 3]

## Failures and how to do differently

- `pg_dump: error: no matching schemas were found` here came from stale registry metadata, not a missing schema -> verify both `public.project.schema_name` and `information_schema.schemata` before assuming the DB is wrong [Task 1]
- False warnings about missing storage files or policies can come from assuming schema name == bucket id == policy prefix -> resolve each naming layer independently before declaring the local project incomplete [Task 2]
- Testing shell helpers from plain PowerShell can hide Git Bash path assumptions (`/bin/bash` not found) -> verify with the same Git Bash path used by the batch workflow before concluding the helper is broken [Task 2]
- A missing-`config.toml` warning in this workflow was a backup-script lookup bug, not an absent config file -> inspect the shared local-supabase repo before treating the environment as incomplete [Task 3]

# Task Group: Angel website SketchUp checkout placeholder flow
scope: Reuse when the user wants a temporary paid-resource checkout placeholder in `angel-interior`, especially a minimal Stripe coming-soon page, a staged redirect flow, and preservation-first edits around live resource pages; not a finalized payment implementation guide.
applies_to: cwd=\\?\C:\Users\user\Desktop\angel-interior; reuse_rule=safe for this checkout if `/checkout/sketchup/` remains a separate route from `/sketchup-free-resources` and the payment flow is still provisional

## Task 1: Define temporary Stripe coming-soon flow for paid SketchUp downloads, uncertain

### rollout_summary_files

- rollout_summaries/2026-05-26T04-17-01-yLXA-angel_stripe_checkout_coming_soon_placeholder.md (cwd=\\?\C:\Users\user\Desktop\angel-interior, rollout_path=C:\Users\user\.codex\sessions\2026\05\26\rollout-2026-05-26T12-17-01-019e6280-1614-70f1-a92c-7d956db49cda.jsonl, updated_at=2026-05-28T02:03:35+00:00, thread_id=019e6280-1614-70f1-a92c-7d956db49cda, user-described placeholder flow but implementation was interrupted)

### keywords

- angel-interior, website-angel-interior, stripe, checkout, /checkout/sketchup/, /sketchup-free-resources, sketchup-free-resources.php, Stripe payment comming soon, 5 sec timer, redirect to download pages, preserve live data

## User preferences

- when the user said, "please do not make my content missing or data missing.. that are using now", future edits in this workspace should default to narrow, non-destructive changes and verify live loaders before touching UI or routes [Task 1]
- when the user described a temporary page saying "Stripe payment comming soon ..." with "a new function timer which wait for 5 sec timer then it will redirect to download pages", treat the request as an interim UX stage rather than a full payment rollout [Task 1]
- when the user connected `/sketchup-free-resources` to `/checkout/sketchup/`, preserve that route split unless the user explicitly asks to merge the paid resource page and checkout path [Task 1]

## Reusable knowledge

- Relevant area for this request was `website-angel-interior/template/sketchup-free-resources.php`, with the user expecting the paid CTA to flow through a separate checkout route [Task 1]
- The user is open to staged payment work here: placeholder page now, then later real Stripe return/download behavior with resource data [Task 1]

## Failures and how to do differently

- The rollout stopped before implementation, so the placeholder page was not built -> do not assume this flow exists in code just because the request was described [Task 1]
- Future agents should confirm the redirect chain explicitly: CTA -> coming-soon page -> final download page, and whether the 5-second auto-redirect belongs only on the placeholder page [Task 1]
- Keep any placeholder isolated from the current resource dataset and live page rendering unless a concrete code path proves a broader change is required [Task 1]

# Task Group: Zenius repo sync, stash recovery, and build verification
scope: Reuse when the user needs `zenius-tech-2026` updated without losing local edits, especially stash/pull/pop recovery on Windows plus immediate build verification; not for `template/`-only design work.
applies_to: cwd=\\?\C:\Users\user\Desktop\zenius and C:\Users\user\Desktop\zenius\zenius-tech-2026; reuse_rule=safe for this Zenius workspace if `zenius-tech-2026` remains the actual Git repo and `npm.cmd run build` still resolves the production build

## Task 1: Preserve local edits, pull remote `main`, and verify build, success

### rollout_summary_files

- rollout_summaries/2026-05-26T07-52-57-MvcG-zenius_pull_stash_pop_build_success.md (cwd=\\?\C:\Users\user\Desktop\zenius, rollout_path=C:\Users\user\.codex\sessions\2026\05\26\rollout-2026-05-26T15-52-57-019e6345-c6f1-7871-aadf-81a6ff38ed1e.jsonl, updated_at=2026-05-26T07:57:08+00:00, thread_id=019e6345-c6f1-7871-aadf-81a6ff38ed1e, stash-first pull workflow ended with clean build and clean git status)

### keywords

- zenius-tech-2026, git stash push -m "before pull", git pull origin main, git stash pop, src/style.css, merge conflict, npm.cmd run build, vue-tsc -b, vite build, git status --short, dubious ownership

## User preferences

- when the safe recovery path was available, the user asked for the exact commands `git stash push -m "before pull"`, `git pull origin main`, `git stash pop` -> in similar Git recovery situations, give the direct command sequence instead of explanation-first guidance [Task 1]
- when the repo sync was done, the user asked `ok if done ai help me npm run build zenius-tech-2026` -> after update/sync work, move straight into build verification rather than waiting for another prompt [Task 1]

## Reusable knowledge

- The actual Git repo is `C:\Users\user\Desktop\zenius\zenius-tech-2026`; `C:\Users\user\Desktop\zenius` is only the parent folder, so repo commands from the parent can mislead or hit Git ownership noise [Task 1]
- In this repo on Windows, `npm.cmd run build` is the reliable production verification path; the build resolves to `vue-tsc -b && vite build` [Task 1]
- If `git pull` is blocked by local edits in files like `src/App.vue` or `src/style.css`, stash-first is a safe preservation path before updating [Task 1]

## Failures and how to do differently

- `git stash pop` can leave stylesheet conflicts even when the pull itself is clean -> assume CSS files may need manual conflict cleanup before build verification [Task 1]
- Patch context can miss conflict markers if the rendered text/encoding differs from the assumed patch context -> inspect the literal marker lines first, then patch surgically [Task 1]
- Running repo checks from `C:\Users\user\Desktop\zenius` instead of `...\zenius-tech-2026` can trigger false path assumptions and "dubious ownership" noise -> verify the actual repo root before diagnosing Git problems [Task 1]

# Task Group: trash-container-app schema-accurate docs, map data, and desktop admin cleanup
scope: Reuse when the user wants `trash-container-app` aligned to the real Supabase `trash` schema, especially doc-first audits, dummy-vs-live data tracing, map coordinates, and desktop order/map UX; not a generic Supabase playbook for other repos.
applies_to: cwd=\\?\C:\Users\user\Desktop\trash-container-app; reuse_rule=safe for this checkout if the root docs and `trash` schema remain the source of truth, but re-check actual table/contracts before changing live data

## Task 1: Read project docs and identify the live workspace truth, success

### rollout_summary_files

- rollout_summaries/2026-05-25T07-58-16-GDPj-trash_container_app_supabase_ui_map_coordinates_cleanup.md (cwd=\\?\C:\Users\user\Desktop\trash-container-app, rollout_path=C:\Users\user\.codex\sessions\2026\05\25\rollout-2026-05-25T15-58-16-019e5e24-4782-7c71-9092-7ebf267a3d69.jsonl, updated_at=2026-05-26T03:43:29+00:00, thread_id=019e5e24-4782-7c71-9092-7ebf267a3d69, root-doc read and current-state routing)

### keywords

- trash-container-app, STATUS.md, DATABASE.md, SYSTEM_MAP.md, PATH_ROUTER.md, IMPLEMENTATION_PLAN.md, PROGRESS.md, web-admin-app, admin-panel-trash, not git repo root

## Task 2: Audit `web-admin-app`, align `DATABASE.md`, and switch map filters to real schema data, success

### rollout_summary_files

- rollout_summaries/2026-05-25T07-58-16-GDPj-trash_container_app_supabase_ui_map_coordinates_cleanup.md (cwd=\\?\C:\Users\user\Desktop\trash-container-app, rollout_path=C:\Users\user\.codex\sessions\2026\05\25\rollout-2026-05-25T15-58-16-019e5e24-4782-7c71-9092-7ebf267a3d69.jsonl, updated_at=2026-05-26T03:43:29+00:00, thread_id=019e5e24-4782-7c71-9092-7ebf267a3d69, page-by-page audit plus live bin-size filter rewrite and Johor Bahru coordinate seeding)

### keywords

- web-admin-app, dummy Vue data, env.IS_MOCK, MapView.vue, driverTasksStore, bin_sizes, task.order.binSize.id, DATABASE.md, trash.orders, latitude, longitude, Johor Bahru, supabase db query, quoted camelCase

## Task 3: Align `admin-panel-trash` order status and coordinate UX to the live contract, success

### rollout_summary_files

- rollout_summaries/2026-05-25T07-58-16-GDPj-trash_container_app_supabase_ui_map_coordinates_cleanup.md (cwd=\\?\C:\Users\user\Desktop\trash-container-app, rollout_path=C:\Users\user\.codex\sessions\2026\05\25\rollout-2026-05-25T15-58-16-019e5e24-4782-7c71-9092-7ebf267a3d69.jsonl, updated_at=2026-05-26T03:43:29+00:00, thread_id=019e5e24-4782-7c71-9092-7ebf267a3d69, desktop order status fix plus coordinate helper and map readiness affordances)

### keywords

- admin-panel-trash, web-antd, OrderStatus.FAILED, order-form.vue, order-detail.vue, order-list.vue, create_order_with_tasks, Coordinate Helper, Map Status, Open Map, latitude, longitude, .vue-global-types, EPERM

## User preferences

- when the user asked to `read my project trash-container-app 3x project folder inside .md and also read root .md to understand what the latest situation`, they wanted a concise root-doc synthesis before deeper code changes -> start with root docs and status docs first, then only dive into code where the docs point [Task 1]
- when the user asked which pages were still using dummy or hardcoded Vue data, they wanted a precise page-by-page audit from code -> trace routes, stores, and views rather than answering generically [Task 2]
- when the user asked to use Supabase data "very accurate", "make sure it really fit", and to use database settings for filtering, default to schema-fit cleanup only and avoid invented labels or speculative UI rewrites [Task 2][Task 3]
- when the user asked to try improving coordinate UX, they wanted a practical admin-side helper rather than a bigger geocoding system [Task 3]

## Reusable knowledge

- In this workspace, `STATUS.md` is the freshest operational summary; `PROGRESS.md` can be stale, and the app `README.md` files are mostly boilerplate compared with the root doc set [Task 1]
- `PATH_ROUTER.md` identifies `admin-panel-trash`, `web-driver-app`, and `web-admin-app` as the 3 primary projects, so route work through those names rather than wandering the whole workspace [Task 1]
- The real `trash` contract includes `attachments`, `customer_transactions`, `driver_bankaccounts`, `driver_tasks`, and `driver_withdrawals`, and the important map path is `orders.latitude` / `orders.longitude` [Task 2]
- `driver_tasks` is the primary execution feed, and the active map flow in `web-admin-app` is driven by `driverTasksStore` joins into `orders`, `bin_sizes`, and `drivers` [Task 2]
- The correct map filter axis in `web-admin-app` is `task.order.binSize.id` / `name`, not hardcoded `green` / `blue` categories; GYOR markers can stay as status overlays while filters come from live `bin_sizes` [Task 2]
- The local `trash.orders` table was successfully seeded with Johor Bahru-area coordinates and verified via read-back for `ORD-TR-0001` through `ORD-TR-0005` [Task 2]
- `admin-panel-trash` already passes `deliveryAddress`, `latitude`, and `longitude` through `create_order_with_tasks`; the schema drift here was missing `failed` order status support and light UI affordances on top [Task 3]
- Vben order forms in this project can be extended with a helper panel beneath the generated form without changing the payload contract, which made the `Coordinate Helper` a low-risk improvement [Task 3]

## Failures and how to do differently

- `git status` at the workspace root failed because `trash-container-app` is not the repo root -> do not assume the top-level workspace is the Git checkout [Task 1]
- `supabase db query` on Windows rejected multiple SQL statements in one prepared statement -> split write and verification into separate one-statement SQL files [Task 2]
- Verification queries against this schema need quoted camelCase identifiers like `"orderNo"` and `"deliveryAddress"` -> missing quotes can make correct data look broken [Task 2]
- `pg_typeof()` caused a scan issue in the CLI envelope -> cast `latitude` / `longitude` to `text` when you need readable DB verification output [Task 2]
- `pnpm typecheck` in `admin-panel-trash/apps/web-antd` hit unrelated workspace/tooling issues (`--ignoreDeprecations` invalid, `.vue-global-types` `EPERM`) -> treat those as environment failures and fall back to targeted read-back verification before blaming the UI edits [Task 3]

# Task Group: Zenius template zone selector redesign
scope: Reuse when the task touches `C:\Users\user\Desktop\zenius\template`, especially presentation-only redesigns of shared selectors/chips across Home and Standings and Windows-safe frontend build verification; not for logic changes or edits to the read-only source app.
applies_to: cwd=\\?\C:\Users\user\Desktop\zenius and C:\Users\user\Desktop\zenius\template; reuse_rule=safe for this Zenius workspace if `template/` remains the editable target and the same selector still appears in both Home and Standings

## Task 1: Update Zone 1/2/3 tag design in `template/`, success

### rollout_summary_files

- rollout_summaries/2026-05-22T01-31-46-A3xU-zone_tag_design_update_template_app.md (cwd=\\?\C:\Users\user\Desktop\zenius, rollout_path=C:\Users\user\.codex\sessions\2026\05\22\rollout-2026-05-22T09-31-46-019e4d4f-5a09-77d3-87dc-f7e7ef313912.jsonl, updated_at=2026-05-22T05:22:58+00:00, thread_id=019e4d4f-5a09-77d3-87dc-f7e7ef313912, unified Home and Standings zone selectors into one shared premium tag style and verified the build)

### keywords

- zenius, template, template-ui-redesign, zone tag, zone selector, HomeView.vue, StandingsView.vue, style.css, zone-tag-rail, zone-tag, npm.cmd, npm.ps1 cannot be loaded because running scripts is disabled on this system, vite build

## User preferences

- when the user asks to update the "Zone 1,Zone 2,Zone 3 tag design", treat it as a visual refresh request, not a logic change [Task 1]
- when the wording is broad and design-focused ("tag design"), default to improving presentation, active state, and cross-screen consistency before changing routing or data behavior [Task 1]

## Reusable knowledge

- The editable redesign target is `template/`; `zenius-tech-2026/` is the read-only source app [Task 1]
- The zone selector existed in two different visual treatments: `HomeView.vue` used the hero action row, while `StandingsView.vue` used a separate inline button row; updating only one leaves the UI inconsistent [Task 1]
- A shared `zone-tag-rail` / `zone-tag` pattern can be reused across both screens, with view-specific polish kept in `template/src/style.css` instead of duplicating styling in each view [Task 1]
- Verification on this machine should use `npm.cmd run build` when PowerShell blocks `npm run build` with `npm.ps1 cannot be loaded because running scripts is disabled on this system.` [Task 1]

## Failures and how to do differently

- CSS patch context mismatch -> re-read the exact live file boundaries and patch against the real line ranges before retrying [Task 1]
- `npm run build` fails under PowerShell execution policy -> rerun the same verification via `npm.cmd run build` and use that result as the real signal [Task 1]

# Task Group: Angel admin local dev startup verification
scope: Reuse when the user wants `admin-panel-angel/apps/web-antd` started locally, especially terse run requests, Windows-safe `pnpm` launch behavior, and Vite listener verification; not a full Angel database/publish runbook.
applies_to: cwd=\\?\C:\Users\user\Desktop\angel-interior and C:\Users\user\Desktop\angel-interior\admin-panel-angel\apps\web-antd; reuse_rule=safe for this Angel checkout if `apps/web-antd` is still the target app and `dev:local` still maps to Vite local mode

## Task 1: Start `dev:local` for `admin-panel-angel/apps/web-antd`, partial but verified listener

### rollout_summary_files

- rollout_summaries/2026-05-20T09-58-29-xDsO-angel_admin_web_antd_dev_local_startup.md (cwd=\\?\C:\Users\user\Desktop\angel-interior, rollout_path=C:\Users\user\.codex\sessions\2026\05\20\rollout-2026-05-20T17-58-29-019e44d2-8c49-7180-9020-cc0838d8568e.jsonl, updated_at=2026-05-20T10:01:56+00:00, thread_id=019e44d2-8c49-7180-9020-cc0838d8568e, first sandbox launch failed, unrestricted retry succeeded, final listener verified on localhost:6006)

### keywords

- angel-interior, admin-panel-angel, apps/web-antd, pnpm.cmd, dev:local, development.localhost, Vite, vite.config.mts, Get-NetTCPConnection, Get-CimInstance Win32_Process, Access is denied, localhost:6006, node.exe

## User preferences

- when the user says `admin-panel-angel pnpm run dev:local this`, treat it as a direct run request, not a planning prompt [Task 1]
- when the active file already points at `apps/web-antd/.env.development.localhost`, check the matching app directory before launching so the run happens from the correct workspace [Task 1]

## Reusable knowledge

- `admin-panel-angel/apps/web-antd/package.json` defines `dev:local` as `pnpm vite --mode development.localhost` [Task 1]
- Windows-safe launch here is `pnpm.cmd run dev:local` from `admin-panel-angel/apps/web-antd` [Task 1]
- The verified listener for this run was `http://localhost:6006/` [Task 1]
- The reliable verification chain was: launch with `pnpm.cmd`, then confirm the listening port and inspect the owning `node.exe` / Vite command line before reporting success [Task 1]

## Failures and how to do differently

- `pnpm run dev:local` fails with `Cannot read directory "../../../../..": Access is denied.` or `Could not resolve "...\\vite.config.mts"` -> the sandbox is blocking Vite/esbuild workspace resolution, so retry outside the sandbox / unrestricted context before debugging app code [Task 1]
- Port probing alone can catch unrelated listeners -> only trust the URL after verifying the owner process is the app's `node.exe` running Vite [Task 1]
