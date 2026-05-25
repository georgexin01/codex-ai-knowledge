<!-- AI GOVERNANCE: MAX 300 LINES. When adding new task groups, trim oldest from bottom. Auto-trim fires on rot-audit when line count exceeds 300. -->

# Task Group: Codex-to-.gemini bridge routing and auto-refresh
scope: Reuse when the user asks Codex to read `.gemini` knowledge/skills/memory, wants a Codex-side bridge instead of a one-off explanation, or needs change-aware routing for `.gemini`; not for generic repo exploration outside the `.codex`/`.gemini` relationship.
applies_to: cwd=\\?\C:\Users\user\Documents\Codex\2026-05-04\ai-add-a-codex-shortcut-at and C:\Users\user\.codex; reuse_rule=safe for this machine's Codex-home knowledge bridge if you re-check the live bridge/router files before editing and avoid assuming `.gemini` native skills map directly to Codex skills

## Task 1: Build a Codex bridge for `.gemini`, success

### rollout_summary_files

- rollout_summaries/2026-05-04T06-04-27-CfIq-codex_gemini_full_access_routing.md (cwd=\\?\C:\Users\user\Documents\Codex\2026-05-04\ai-add-a-codex-shortcut-at, rollout_path=C:\Users\user\.codex\archived_sessions\rollout-2026-05-04T14-04-27-019df196-8715-7ab2-84c7-33cd1d9b96de.jsonl, updated_at=2026-05-04T06:15:48+00:00, thread_id=019df196-8715-7ab2-84c7-33cd1d9b96de, created the Codex-side read-order bridge and folder relationship map)

### keywords

- .gemini, .codex, GEMINI_FULL_ACCESS_ROUTING.md, AGENTS.md, route.yaml, GEMINI.md, ROUTER.idx, ATLAS.idx, GROUND_KERNEL.md, EXECUTION_KERNEL.md, folder relationship, knowledge bridge

## Task 2: Build dynamic router and auto-refresh loop for `.gemini`, success

### rollout_summary_files

- rollout_summaries/2026-05-04T06-04-27-CfIq-codex_gemini_full_access_routing.md (cwd=\\?\C:\Users\user\Documents\Codex\2026-05-04\ai-add-a-codex-shortcut-at, rollout_path=C:\Users\user\.codex\archived_sessions\rollout-2026-05-04T14-04-27-019df196-8715-7ab2-84c7-33cd1d9b96de.jsonl, updated_at=2026-05-04T06:15:48+00:00, thread_id=019df196-8715-7ab2-84c7-33cd1d9b96de, added manifest-based change detection, generated routing, and a watcher startup path)

### keywords

- Update-GeminiRouting.ps1, Watch-GeminiRouting.ps1, GEMINI_DYNAMIC_ROUTING.md, gemini-manifest.json, last-changes.json, watcher.log, FileSystemWatcher, Get-ChildItem, Access is denied, SESSION_SHADOW.json, Startup shortcut, safe indexed files

## User preferences

- when the user asked for "a full access routing" so AI could use ".gemini knowledge or skills and others folder exist and knowing what they are used for and how they connected each other their relationship", default to a durable Codex-side bridge and relationship map, not a one-time folder listing [Task 1]
- when the user asks Codex to "understand and read those nessasary fiels and folder", route through compact discovery/index files first so the bridge stays navigable instead of turning into a broad tree dump [Task 1]
- when the user asks for "auto rerouting when any changes had happen in .gemini folder or files changes" and to "redo routing for those changed files in .codex", default to change-aware regeneration with Codex-owned outputs instead of static notes [Task 2]

## Reusable knowledge

- The durable read order here is: `GEMINI_FULL_ACCESS_ROUTING.md` -> `route.yaml` / `GEMINI.md` fallback context -> `ROUTER.idx` -> `ATLAS.idx` -> kernel files; this keeps `.gemini` hydration route-first instead of broad-crawl first [Task 1]
- `ROUTER.idx` and `ATLAS.idx` are the best first-pass discovery anchors when the user asks Codex to read `.gemini` knowledge [Task 1]
- `.gemini` can be reused from Codex by writing Codex-side bridge/router artifacts; Gemini/Claude workflows are reference material unless converted into native `C:\Users\user\.codex\skills\<skill-name>\SKILL.md` [Task 1]
- Safe `.gemini` change detection can be done with manifest + hash comparison so routing rewrites happen only when real file changes occur [Task 2]
- A user-level Startup shortcut plus hidden watcher is a workable fallback when scheduled-task creation fails on Windows [Task 2]
- `SESSION_SHADOW.json` is intended memory in this environment and should not be excluded just because the filename contains `session` [Task 2]

## Failures and how to do differently

- `route.yaml` appears to be the obvious source of truth but points at a missing `antigravity\route.yaml` -> fall back to `GEMINI.md`, `ROUTER.idx`, `ATLAS.idx`, and the kernel files before concluding the bridge is broken [Task 1]
- Broad `.gemini` hydration creates noise and token waste -> use indexes first and only deepen into the relevant subtree after the route is established [Task 1][Task 2]
- `rg --files` returns `Access is denied` on this machine for some `.gemini` scans -> switch to PowerShell `Get-ChildItem` inventory instead of fighting the failing tool choice [Task 2]
- Scheduled-task setup fails with `Access is denied` -> use the user Startup shortcut + hidden watcher path instead of blocking on admin-only automation [Task 2]
- An over-broad secret/session exclusion can hide real memory like `SESSION_SHADOW.json` -> verify filename filters against known keepers before finalizing the router [Task 2]

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
