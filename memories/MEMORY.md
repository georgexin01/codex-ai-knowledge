# Task Group: EcoWorld `.gemini` routing hydration and UI note retrieval
scope: Reuse when the user asks to read `.gemini` knowledge while working in `EcoWorld`, especially when the goal is to hydrate routing and pull the active website/UI note without broad tree reads.
applies_to: cwd=\\?\C:\Users\user\Desktop\ecoworld and adjacent EcoWorld design-context requests that depend on Codex-to-Gemini routing; reuse_rule=safe for this EcoWorld checkout and similar `.gemini` hydration requests if you re-check the current generated route, indexed note paths, and fallback chain first

## Task 1: Read `.gemini` knowledge for EcoWorld website context, success

### rollout_summary_files

- rollout_summaries/2026-05-12T07-38-02-n2DH-read_gemini_knowledge_ecoworld_routing_hydration.md (cwd=\\?\C:\Users\user\Desktop\ecoworld, rollout_path=C:\Users\user\.codex\sessions\2026\05\12\rollout-2026-05-12T15-38-02-019e1b1f-13ff-7b63-958c-8335a88c5fdd.jsonl, updated_at=2026-05-12T07:39:07+00:00, thread_id=019e1b1f-13ff-7b63-958c-8335a88c5fdd, hydrated the bridge/index path and loaded the active EcoWorld UI note)

### keywords

- ai read .gemini knowledge, EcoWorld, ECOWORLD_IMPLEMENTED_UI_NOTES_2026-05-12.md, GEMINI_DYNAMIC_ROUTING.md, Update-GeminiRouting.ps1, ROUTER.idx, ATLAS.idx, GROUND_KERNEL.md, EXECUTION_KERNEL.md, skill_path_router

## User preferences

- when the user says `ai read .gemini knowledge`, treat it as a direct hydration trigger and load the Codex-to-Gemini bridge/index path without stopping for clarifying questions [Task 1]
- when the request happens inside `C:\Users\user\Desktop\ecoworld` and an EcoWorld UI note is already active, narrow the `.gemini` read to the current website/design context instead of doing a broad arbitrary crawl [Task 1]

## Reusable knowledge

- The validated order on this machine is `C:\Users\user\.codex\00_CODEX_START_HERE.md` -> `C:\Users\user\.codex\GEMINI_FULL_ACCESS_ROUTING.md` -> `Update-GeminiRouting.ps1 -Quiet` -> `C:\Users\user\.codex\GEMINI_DYNAMIC_ROUTING.md` -> `C:\Users\user\.gemini\route.yaml` -> `GEMINI.md` -> `ROUTER.idx` -> `ATLAS.idx` -> `GROUND_KERNEL.md` -> `EXECUTION_KERNEL.md` -> `skill_path_router.md` [Task 1]
- `GEMINI_DYNAMIC_ROUTING.md` confirmed `C:\Users\user\.gemini\antigravity\skills\design\website\ECOWORLD_IMPLEMENTED_UI_NOTES_2026-05-12.md` was indexed, making that note a strong first retrieval handle for future EcoWorld website/design follow-ups [Task 1]
- `ROUTER.idx` and `ATLAS.idx` are the intended compact discovery layer after the bridge files; use them to keep `.gemini` hydration route-driven instead of reading the whole tree [Task 1]

## Failures and how to do differently

- Symptom: `.gemini` hydration turns into a broad, noisy crawl. Cause: skipping the bridge/index path and reading the tree opportunistically. Fix: follow the bridge order, refresh the router, and jump through `ROUTER.idx`/`ATLAS.idx` plus the active EcoWorld note [Task 1]
- No functional failure occurred in this rollout; the meaningful lesson is to keep the read scope narrow and route-driven because the bridge explicitly warns against full-tree hydration [Task 1]

# Task Group: EcoWorld project-root cleanup and PHP asset cache busting
scope: Reuse for EcoWorld maintenance tasks that trim disposable project-root artifacts or need shared PHP asset cache busting so CSS/JS updates load immediately; not a generic cleanup recipe for unrelated repos.
applies_to: cwd=\\?\C:\Users\user\Desktop\ecoworld and close variants of the same checkout; reuse_rule=safe when the task is in this EcoWorld repo family and you re-check live folder references, shared include points, and runtime relevance before deleting or centralizing anything

## Task 1: Remove disposable EcoWorld root folders, success

### rollout_summary_files

- rollout_summaries/2026-05-12T05-53-52-ykaJ-ecoworld_cleanup_and_php_asset_cache_busting.md (cwd=\\?\C:\Users\user\Desktop\ecoworld, rollout_path=C:\Users\user\.codex\sessions\2026\05\12\rollout-2026-05-12T13-53-52-019e1abf-b5e0-7652-bdb8-3f1678449c59.jsonl, updated_at=2026-05-12T07:37:49+00:00, thread_id=019e1abf-b5e0-7652-bdb8-3f1678449c59, removed `_reference`, `tmp`, and `test-results` after checking runtime relevance)

### keywords

- EcoWorld, cleanup, tmp, test-results, cdp-profile, layout-check.mjs, BLUEPRINT.md, Test-Path, not a git repository, filesystem hygiene

## Task 2: Add second-precision PHP asset versioning in shared includes, success

### rollout_summary_files

- rollout_summaries/2026-05-12T05-53-52-ykaJ-ecoworld_cleanup_and_php_asset_cache_busting.md (cwd=\\?\C:\Users\user\Desktop\ecoworld, rollout_path=C:\Users\user\.codex\sessions\2026\05\12\rollout-2026-05-12T13-53-52-019e1abf-b5e0-7652-bdb8-3f1678449c59.jsonl, updated_at=2026-05-12T07:37:49+00:00, thread_id=019e1abf-b5e0-7652-bdb8-3f1678449c59, added `ECO_ASSET_VERSION` and wired shared CSS/JS query strings)

### keywords

- EcoWorld, php, cache-busting, style.css, app.js, htmlHead.php, htmlBody.php, init.php, ECO_ASSET_VERSION, date('YmdHis'), php -l

## User preferences

- when the user asked to remove "all unessasary thing like testing or folder that are empty or are lagacy no use anymore", default to trimming clearly disposable legacy/test/empty items, but still verify runtime relevance before deleting them [Task 1]
- when the user confirmed `tmp` and `test-results` with "remove then", prefer direct deletion of disposable QA/temp folders instead of preserving them for history [Task 1]
- when the user said "set <?= datetime ?> with min sec" so CSS updates load, prefer PHP-generated cache busting in shared includes rather than per-page manual edits [Task 2]
- when the user asked to do it for "other css that need updating", update the shared asset entry points centrally when they exist [Task 2]

## Reusable knowledge

- In this EcoWorld checkout, `test-results` held QA artifacts and a large `cdp-profile` browser cache, while `tmp` held local server logs and temp content; both were safe to remove once the user wanted a lean project root [Task 1]
- `test-results/layout-check.mjs` was referenced in `BLUEPRINT.md`, so test/QA folders still need reference checks before deletion even when they look disposable [Task 1]
- The repo root was not a git repo, so `Test-Path` and direct directory inspection were the working verification path for cleanup instead of git state [Task 1]
- `lib/init.php` is the shared bootstrap for EcoWorld templates, and `lib/htmlHead.php` / `lib/htmlBody.php` are the shared CSS/JS include points; those are the right first places to inspect for global asset-versioning changes [Task 2]
- The validated cache-busting pattern here is `define('ECO_ASSET_VERSION', date('YmdHis'));` in `lib/init.php`, then `/css/style.css?v=<?= h(ECO_ASSET_VERSION) ?>` and `/js/app.js?v=<?= h(ECO_ASSET_VERSION) ?>` in the shared include files [Task 2]
- `php -l` on `init.php`, `htmlHead.php`, and `htmlBody.php` was the syntax validation step after the shared include edits [Task 2]

## Failures and how to do differently

- Symptom: cleanup candidates look unused, but deleting them could break runtime placeholders or referenced QA utilities. Cause: some empty or test-like folders in this repo are still meaningful. Fix: grep/check references like `BLUEPRINT.md` first, then remove only the disposable parts or wait for explicit confirmation before deleting the whole folder [Task 1]
- Symptom: git-based cleanliness checks are unavailable. Cause: the EcoWorld root is not a git repo and `git status` returns `not a git repository`. Fix: verify deletions with `Test-Path` and direct filesystem inspection instead of assuming git state exists [Task 1]
- Symptom: patching a shared PHP include fails on line/context match. Cause: file encoding or line structure is brittle, especially in `htmlHead.php`. Fix: use exact string replacement when patch context is unreliable, then re-run `php -l` on every edited shared include [Task 2]

# Task Group: EcoWorld design workflow, free visual assets, and homepage filter UI
scope: Reuse when working in `EcoWorld` or similar site-refresh tasks that need brand-grounded UI updates plus a non-paid image fallback; not a generic image-generation recipe.
applies_to: cwd=\\?\C:\Users\user\Desktop\ecoworld and related cross-agent skill updates triggered by EcoWorld image/design requests; reuse_rule=safe for this EcoWorld checkout and similar "no image-generation tool available" design tasks if you re-check live asset/tool availability and current brand references first

## Task 1: Persist free visual asset fallback into Gemini/Codex skills, success

### rollout_summary_files

- rollout_summaries/2026-05-11T04-11-42-EmJp-ecoworld_free_visual_assets_and_modern_filter_ui.md (cwd=\\?\C:\Users\user\Desktop\ecoworld, rollout_path=C:\Users\user\.codex\sessions\2026\05\11\rollout-2026-05-11T12-11-42-019e153b-d3aa-73c3-8c94-575c0ce75cf7.jsonl, updated_at=2026-05-11T10:51:20+00:00, thread_id=019e153b-d3aa-73c3-8c94-575c0ce75cf7, encoded the fallback in shared Gemini/Codex skills and project notes)

### keywords

- EcoWorld, free visual assets, Unsplash, Pexels, Pixabay, Material Symbols, SVG, CSS art, image generation fallback, FREE_VISUAL_ASSET_SOURCING.md, free-visual-assets, BLUEPRINT.md

## Task 2: Modernize EcoWorld homepage filter/search controls, success

### rollout_summary_files

- rollout_summaries/2026-05-11T04-11-42-EmJp-ecoworld_free_visual_assets_and_modern_filter_ui.md (cwd=\\?\C:\Users\user\Desktop\ecoworld, rollout_path=C:\Users\user\.codex\sessions\2026\05\11\rollout-2026-05-11T12-11-42-019e153b-d3aa-73c3-8c94-575c0ce75cf7.jsonl, updated_at=2026-05-11T10:51:20+00:00, thread_id=019e153b-d3aa-73c3-8c94-575c0ce75cf7, refreshed the filter panel toward the real EcoWorld white/green site language)

### keywords

- EcoWorld, filter panel, chip scroller, scrollbar, information.txt, lib/components.php, css/style.css, white-green brand, masonry layout, filter-selects

## User preferences

- when the user said they had no image-generation tool and asked to "generate images for my project ecoworld ... using above technique," default to a durable stock/icon/SVG/CSS fallback workflow instead of waiting on raster generation access [Task 1]
- when the user asked to "write inside my codex or gemini knowledge if need for images generating" and to "update to claude code skills," persist the workflow in skills/knowledge and project notes rather than leaving it as chat-only advice [Task 1]
- when the user asked to "look into information.txt url see how ecoworld is look like the design theme and card, text, border... button..," future EcoWorld redesigns should anchor on the real brand/site reference rather than generic modern styling [Task 2]
- when the user asked "allow the scrolling bar to be invisible, css can change the width and color.. to 0.," horizontal chip/scroll areas should keep scroll behavior but hide the scrollbar visually by default [Task 2]

## Reusable knowledge

- The shared non-paid fallback was formalized at `C:\Users\user\.gemini\antigravity\skills\normal\design\FREE_VISUAL_ASSET_SOURCING.md`, and the rollout also added the native Codex skill `C:\Users\user\.codex\skills\free-visual-assets\SKILL.md` so future sessions can trigger the same behavior quickly [Task 1]
- The free visual workflow order that worked here is: project-owned assets first, then `Unsplash`/`Pexels`/`Pixabay`, then `Material Symbols` or other open icons, then `SVG`/`CSS art`, then local caching plus source/license notes in `IMAGE_SOURCES.md` or `BLUEPRINT.md` [Task 1]
- The Gemini website/app skills and Claude-facing image skills were updated to point at the fallback, so "no image tool available" is now a documented workflow instead of a dead end [Task 1]
- EcoWorld filter-panel work lives around `lib/components.php` plus `css/style.css` selectors such as `filter-panel`, `chip-row`, `chip`, and `filter-selects`; the refreshed panel uses a cleaner white/green surface, softer border/shadow, search-icon treatment, polished chip states, and custom select chevrons [Task 2]
- The page remains a lazy-loaded masonry layout; filter redesigns should preserve the existing no-horizontal-overflow and mobile-collapse behavior that already passed validation [Task 2]

## Failures and how to do differently

- Symptom: image requests stall because there is no working image-generation tool. Cause: assuming raster generation is the primary path. Fix: pivot immediately to the stored free-visual workflow and cache selected assets locally instead of waiting on unavailable tooling [Task 1]
- Symptom: appending guidance into existing skill files fails. Cause: the exact file tail/context drifted, so exact-match patches missed. Fix: inspect the real tail first and use a direct append only after the target boundary is clear [Task 1]
- Symptom: CSS restyle patches fail or land in the wrong place. Cause: the live `style.css` block drifted from the expected context. Fix: inspect the exact current filter-panel block before patching [Task 2]
- Symptom: the design starts to feel generically "premium" instead of EcoWorld-specific. Cause: styling is being invented without the real site reference. Fix: read `information.txt` and the live EcoWorld page first, then match the actual white/green card, border, text, and button language [Task 2]
- Symptom: scrollbar polish removes chip scrolling. Cause: hiding overflow instead of hiding the scrollbar UI. Fix: keep horizontal scroll enabled and use `scrollbar-width` / `::-webkit-scrollbar` rules to make the scrollbar invisible [Task 2]

# Task Group: Windows Codex `.gemini` bridge and dynamic routing
scope: Reuse when the task involves making Codex understand, route into, or auto-refresh against `C:\Users\user\.gemini` from the user's Windows Codex home; not a general knowledge-management recipe for other machines.
applies_to: cwd=\\?\C:\Users\user\Documents\Codex\2026-05-04\ai-add-a-codex-shortcut-at and Windows Codex home workflows touching C:\Users\user\.codex plus C:\Users\user\.gemini; reuse_rule=safe for this user's Windows `.codex`/`.gemini` bridge and similar cross-agent routing work, but re-check live generated counts, paths, and PowerShell policy behavior before reusing on another machine or account

## Task 1: Build Codex bridge for `.gemini`, success

### rollout_summary_files

- rollout_summaries/2026-05-04T06-04-27-CfIq-codex_gemini_full_access_routing.md (cwd=\\?\C:\Users\user\Documents\Codex\2026-05-04\ai-add-a-codex-shortcut-at, rollout_path=C:\Users\user\.codex\archived_sessions\rollout-2026-05-04T14-04-27-019df196-8715-7ab2-84c7-33cd1d9b96de.jsonl, updated_at=2026-05-04T06:15:48+00:00, thread_id=019df196-8715-7ab2-84c7-33cd1d9b96de, created the durable Codex-side bridge and folder relationship map)

### keywords

- .gemini, .codex, GEMINI_FULL_ACCESS_ROUTING.md, AGENTS.md, route.yaml, ROUTER.idx, ATLAS.idx, GROUND_KERNEL.md, EXECUTION_KERNEL.md, skill_path_router, antigravity\knowledge, antigravity\memory, antigravity\skills

## Task 2: Build dynamic router + auto-refresh, success

### rollout_summary_files

- rollout_summaries/2026-05-04T06-04-27-CfIq-codex_gemini_full_access_routing.md (cwd=\\?\C:\Users\user\Documents\Codex\2026-05-04\ai-add-a-codex-shortcut-at, rollout_path=C:\Users\user\.codex\archived_sessions\rollout-2026-05-04T14-04-27-019df196-8715-7ab2-84c7-33cd1d9b96de.jsonl, updated_at=2026-05-04T06:15:48+00:00, thread_id=019df196-8715-7ab2-84c7-33cd1d9b96de, added manifest-based regeneration and a user-level watcher)

### keywords

- GEMINI_DYNAMIC_ROUTING.md, Update-GeminiRouting.ps1, Watch-GeminiRouting.ps1, gemini-manifest.json, last-changes.json, watcher.log, FileSystemWatcher, Startup shortcut, schtasks, Access is denied, SESSION_SHADOW.json, Get-ChildItem, safe indexed files

## User preferences

- when the user asked for "a full access routing" that lets AI use ".gemini knowledge or skills and others folder exist", they were asking for a durable Codex-side navigation layer, not just a one-time explanation [Task 1]
- when the user asked to know "what they are used for and how they connected each other their relationship", future similar work should proactively map folder purpose and relationships, not just list paths [Task 1]
- when the user wanted the system to "understand and read those nessasary fiels and folder", default to a real bridge/read-order document in `.codex` when cross-agent knowledge reuse is requested [Task 1]
- when the user asked for auto rerouting "when any changes had happen in .gemini folder or files changes", future work should default to change-aware regeneration rather than a static snapshot [Task 2]
- when the user asked the AI to "redo routing for those changed files in .codex" and wanted "full control router in .codex", generate Codex-owned routing artifacts plus a refresh loop instead of leaving the logic implicit [Task 2]

## Reusable knowledge

- `C:\Users\user\.codex\GEMINI_FULL_ACCESS_ROUTING.md` is the durable Codex-side bridge for `.gemini`; it captures read order, priority boundaries, folder roles, and relationship maps so future agents do not have to rediscover the structure from scratch [Task 1]
- `.gemini\route.yaml` pointed to `.\antigravity\route.yaml`, but that target was missing during bridge creation. The proven fallback chain is `GEMINI.md`, `ROUTER.idx`, `ATLAS.idx`, `GROUND_KERNEL.md`, `EXECUTION_KERNEL.md`, then `skill_path_router.md` [Task 1]
- `antigravity\knowledge` is the curated knowledge library, `antigravity\memory` is historical memory/context that should be verified against current files, and `antigravity\skills` are reference workflows rather than native Codex skills unless converted into `C:\Users\user\.codex\skills\<name>\SKILL.md` [Task 1]
- `ROUTER.idx` and `ATLAS.idx` are the best first-pass discovery anchors. Do not hydrate the whole `.gemini` tree when routing can be narrowed through those indexes [Task 1]
- `C:\Users\user\.codex\gemini-router\Update-GeminiRouting.ps1` scans `C:\Users\user\.gemini`, excludes secrets/browser profiles/caches/runtime noise, classifies files, computes SHA256 hashes, emits a manifest, and generates `C:\Users\user\.codex\GEMINI_DYNAMIC_ROUTING.md` plus `last-changes.json` [Task 2]
- Safe `.gemini` change detection can be done with a manifest + hash comparison, avoiding unnecessary rewrites when nothing changed [Task 2]
- In this environment, `Get-ChildItem` was the reliable inventory command while `rg --files` hit `Access is denied` [Task 2]
- The working auto-refresh setup was a hidden PowerShell watcher script plus `C:\Users\user\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup\Codex Gemini Router Watcher.lnk`; the rollout verified the dynamic route after a second regeneration pass and reported `603` safe indexed files at that time [Task 2]
- `SESSION_SHADOW.json` belongs in the memory route for this environment and should not be excluded just because its filename contains `session` [Task 2]

## Failures and how to do differently

- Symptom: routing from `.gemini` feels noisy or incomplete. Cause: treating `.gemini` as a flat folder or relying on `route.yaml` alone even though it pointed to a missing `antigravity\route.yaml`. Fix: use the routing/index files first and fall back to `GEMINI.md`, `ROUTER.idx`, `ATLAS.idx`, and kernel files [Task 1]
- Symptom: someone wants Codex to "use" Gemini skills directly. Cause: Gemini/Claude skill files were treated like native Codex skills. Fix: keep them as reference workflows until they are rewritten into `C:\Users\user\.codex\skills\<name>\SKILL.md` [Task 1]
- Symptom: file inventory or refresh automation fails on Windows. Cause: `rg --files` and scheduled-task creation were blocked with `Access is denied`. Fix: use PowerShell `Get-ChildItem` for inventory and switch to a user-level Startup shortcut plus hidden watcher if `schtasks` is blocked [Task 2]
- Symptom: generated routing silently drops memory files like `SESSION_SHADOW.json`. Cause: the filename exclusion filter is too broad. Fix: validate the filter against known memory files before finalizing exclusions [Task 2]
- Symptom: generated Markdown from the update script is malformed. Cause: unsafe PowerShell quoting/interpolation in the first script version. Fix: use safer string interpolation/output formatting before trusting regenerated route text [Task 2]

# Task Group: quizLAA Vue app Vite/Supabase mode alignment and build
scope: Reuse when working on `webApp-LAA-quiz-v2` or closely related `quizLAA` Vue apps that need Supabase env wiring, Vite mode alignment, or a production build runbook; not a general Vite guide.
applies_to: cwd=\\?\C:\Users\user\Desktop\quizLAA and c:\Users\user\Desktop\quizLAA\webApp-LAA-quiz-v2; reuse_rule=safe for this quizLAA/admin-panel family and similar checkouts that intentionally mirror `admin-panel-quizLaa`; re-check exact env values and scripts before reusing in unrelated repos

## Task 1: Compare admin-panel Supabase wiring to webApp-LAA-quiz-v2 and mirror the mode contract, success

### rollout_summary_files

- rollout_summaries/2026-04-30T10-32-40-XyzV-webapp_laa_quiz_v2_admin_panel_supabase_mode_and_build.md (cwd=\\?\C:\Users\user\Desktop\quizLAA, rollout_path=C:\Users\user\.codex\sessions\2026\04\30\rollout-2026-04-30T18-32-40-019dddf2-a7f0-7032-8c64-6dd8c8c60c93.jsonl, updated_at=2026-04-30T10:49:53+00:00, thread_id=019dddf2-a7f0-7032-8c64-6dd8c8c60c93, aligned the web app to the admin panel's explicit Vite mode contract)

### keywords

- admin-panel-quizLaa, webApp-LAA-quiz-v2, Vite modes, development.localhost, development.supabase, production, Supabase, .env.development.localhost, .env.development.supabase, .env.production, vite.loadEnv, api.zeta-groups.com, localhost:54321, localhost:8001

## Task 2: Build webApp-LAA-quiz-v2, success

### rollout_summary_files

- rollout_summaries/2026-04-30T10-32-40-XyzV-webapp_laa_quiz_v2_admin_panel_supabase_mode_and_build.md (cwd=\\?\C:\Users\user\Desktop\quizLAA, rollout_path=C:\Users\user\.codex\sessions\2026\04\30\rollout-2026-04-30T18-32-40-019dddf2-a7f0-7032-8c64-6dd8c8c60c93.jsonl, updated_at=2026-04-30T10:49:53+00:00, thread_id=019dddf2-a7f0-7032-8c64-6dd8c8c60c93, production build succeeded with `npm.cmd run build`)

### keywords

- webApp-LAA-quiz-v2, npm.cmd, npm.ps1, PowerShell execution policy, vite build, esbuild, spawn EPERM, dist/assets/index-DlmYmjBl.js, build, production

## User preferences

- when the user asked to "learn from admin-panel-quizLaa" and "research and see how the vben admin is connected to supabase local", future similar work should start from the admin panel as the reference implementation rather than inventing a fresh env layout [Task 1]
- when the user asked for the web app's API connection and production env to match that pattern, preserve explicit local/remote/production separation instead of collapsing everything into one generic Vite mode [Task 1]
- when the user said "so help me build npm run build webApp-LAA-quiz-v2", go straight to the project folder and run the build instead of re-explaining config that was already settled [Task 2]

## Reusable knowledge

- `admin-panel-quizLaa` is the clearest reference implementation in this repo family for local Supabase wiring and Vite mode naming. It uses explicit modes `development.localhost`, `development.supabase`, and `production`, with scripts in `apps/web-antd/package.json` mapping those modes to local Docker Supabase, tunnel-based Supabase, and production build behavior [Task 1]
- The mode/env split that worked here was `development.localhost` -> `http://localhost:54321`, `development.supabase` -> `http://localhost:8001`, and `production` -> `https://api.zeta-groups.com` [Task 1]
- `webApp-LAA-quiz-v2/src/config/env.ts` reads `VITE_*` values through a typed wrapper, so auth/API behavior depends on the correct Vite mode file being loaded; `vite.loadEnv` was the verification step that confirmed the right URLs for each mode [Task 1]
- The web app patch that matched the admin pattern added explicit scripts in `package.json` and added `.env.development.localhost` plus `.env.development.supabase`; the existing generic `dev`/`build` setup was not explicit enough for this repo's local-vs-tunnel-vs-production split [Task 1]
- For this repo on Windows PowerShell, `npm.cmd run build` is the reliable build command when the `npm.ps1` shim is blocked by execution policy [Task 2]
- A successful production build produced output under `webApp-LAA-quiz-v2/dist`, including `dist/assets/index-DlmYmjBl.js`, which is a useful fast sanity check when asked whether the build completed [Task 2]

## Failures and how to do differently

- Symptom: Vue app has only generic `dev`/`build` scripts and local Supabase behavior is easy to misconfigure. Cause: the project does not preserve the admin panel's explicit mode naming. Fix: default to the same three-mode structure and separate env files instead of relying on a plain `vite`/generic `.env` arrangement [Task 1]
- Symptom: `npm run build` fails in PowerShell before the actual build starts. Cause: `npm.ps1` is blocked by execution policy. Fix: rerun with `npm.cmd run build` [Task 2]
- Symptom: Vite/esbuild build fails with `spawn EPERM`. Cause: helper-process spawning is blocked. Fix: rerun with permission to spawn the toolchain; do not spend time debugging app code until process permissions are ruled out [Task 2]
