## User Profile

The user uses Codex as a local Windows coding partner and repeatedly asks for durable outcomes that future agents can reuse without re-learning the setup. They work across project checkouts and Codex-home infrastructure, and they prefer important workflows to be persisted into bridge docs, skills, notes, or project artifacts rather than left as chat-only guidance.

They often steer by pointing at a concrete source of truth: a reference repo, the real live site/theme, or the local `.gemini` knowledge graph. In practice, they want the agent to read the real thing first, then act. For `.gemini` requests, they expect direct hydration through the Codex bridge and indexes. For design work, they want updates grounded in the actual brand/site reference rather than generic styling. For project maintenance, they prefer lean roots, central shared fixes, and direct cleanup of disposable artifacts once runtime safety has been checked.

Environment evidence is Windows PowerShell. Shell policy and permissions can matter: `npm.ps1` may be blocked, `Access is denied` can affect inventory or scheduler workflows, and PowerShell-friendly fallbacks are often the fastest path.

## User preferences

- When the user says `ai read .gemini knowledge`, treat it as a direct hydration trigger and load the Codex-to-Gemini bridge/index path without stopping for clarifying questions.
- When `.gemini` is being read in an active checkout like `C:\Users\user\Desktop\ecoworld`, narrow the hydration to the current project context and active note instead of doing a broad arbitrary crawl.
- When the user asks for "a full access routing" so AI can use ".gemini knowledge or skills and others folder exist", treat that as a request for a durable Codex-side navigation layer, not a one-time explanation.
- When the user asks what folders "are used for and how they connected each other their relationship", proactively map folder purpose and relationships instead of only listing paths.
- When the user wants the system to "understand and read those nessasary fiels and folder", prefer writing a real bridge/read-order artifact in `.codex` when cross-agent knowledge reuse is involved.
- When the user asks for auto rerouting "when any changes had happen in .gemini folder or files changes", default to change-aware regeneration and refresh automation rather than static docs.
- When the user asks to "redo routing for those changed files in .codex" and wants "full control router in .codex", generate Codex-owned route artifacts plus a refresh loop instead of leaving the routing logic implicit.
- When the user says they have no image-generation tool and asks to "generate images for my project ecoworld ... using above technique", default to a durable free-asset workflow instead of blocking on raster generation.
- When the user asks to "write inside my codex or gemini knowledge if need for images generating" and to "update to claude code skills", persist the workflow in skills/knowledge and project notes rather than leaving it as chat-only advice.
- When the user asks to "look into information.txt url see how ecoworld is look like the design theme and card, text, border... button..", base EcoWorld UI work on the real site/theme reference instead of generic modern styling.
- When the user asks to "allow the scrolling bar to be invisible, css can change the width and color.. to 0.", keep horizontal scrolling but hide the scrollbar visually by default.
- When the user asks to remove "all unessasary thing like testing or folder that are empty or are lagacy no use anymore", default to trimming clearly disposable legacy/test/empty items, but still verify runtime relevance before deleting them.
- When the user confirms disposable folders with "remove then", prefer direct deletion of QA/temp artifacts instead of keeping them around for history.
- When the user says "set <?= datetime ?> with min sec" so CSS updates load, prefer PHP-generated cache busting in shared includes rather than per-page manual edits.
- When the user asks to do it for "other css that need updating", update the shared asset entry points centrally when they exist.
- When the user says to "learn from admin-panel-quizLaa" or "research and see how the vben admin is connected to supabase local", start from that repo as the source of truth instead of inventing a new convention.
- When matching `webApp-LAA-quiz-v2` to the admin panel, preserve explicit local/remote/production separation instead of flattening env handling into one generic Vite mode.
- When the user asks to "help me build npm run build webApp-LAA-quiz-v2", move directly to the project folder and run the build rather than re-explaining the already-agreed config approach.

## General Tips

- For `.gemini`-related work, the proven first-pass route is `C:\Users\user\.codex\00_CODEX_START_HERE.md`, then `C:\Users\user\.codex\GEMINI_FULL_ACCESS_ROUTING.md`, then `Update-GeminiRouting.ps1 -Quiet`, then `C:\Users\user\.codex\GEMINI_DYNAMIC_ROUTING.md`, then `.gemini` indexes and kernel files.
- Do not treat `.gemini` as a flat tree. If `route.yaml` points to a missing target, fall back to `GEMINI.md`, `ROUTER.idx`, `ATLAS.idx`, `GROUND_KERNEL.md`, `EXECUTION_KERNEL.md`, and `skill_path_router.md`.
- `ROUTER.idx` and `ATLAS.idx` are the preferred compact discovery layer after the bridge files; use them to keep hydration route-driven.
- Gemini/Claude skills are reference workflows only until they are converted into `C:\Users\user\.codex\skills\<name>\SKILL.md`.
- In this environment, `Get-ChildItem` is a safer inventory fallback when `rg --files` hits `Access is denied`.
- If Windows blocks scheduled-task creation for background automation, a user-level Startup shortcut plus a hidden PowerShell watcher is the proven fallback.
- Validate exclusion filters against known good memory files like `SESSION_SHADOW.json`; do not drop them just because a filename contains `session`.
- For EcoWorld `.gemini` follow-ups, `C:\Users\user\.gemini\antigravity\skills\design\website\ECOWORLD_IMPLEMENTED_UI_NOTES_2026-05-12.md` is a strong first retrieval handle once the dynamic route confirms it is indexed.
- For design work without image-generation access, the proven fallback order is project-owned assets, then `Unsplash`/`Pexels`/`Pixabay`, then open icons like `Material Symbols`, then `SVG`/`CSS art`, then local caching plus source/license notes.
- For EcoWorld UI refreshes, search `information.txt`, `lib/components.php`, `css/style.css`, `filter-panel`, `chip-row`, and `filter-selects` first; preserve the lazy masonry layout and no-horizontal-overflow behavior while polishing the controls.
- For EcoWorld maintenance work, check `BLUEPRINT.md` and shared include files before deleting folders or patching assets; `tmp` and `test-results` were disposable here, but some empty-looking directories can still be runtime placeholders.
- For EcoWorld CSS/JS reload issues, inspect `lib/init.php`, `lib/htmlHead.php`, and `lib/htmlBody.php` first; the validated shared pattern is `ECO_ASSET_VERSION = date('YmdHis')` plus `?v=<?= h(ECO_ASSET_VERSION) ?>`, then `php -l` on each edited file.
- For the `quizLAA` family, search `development.localhost`, `development.supabase`, `production`, and `vite.loadEnv` before changing Supabase env wiring.
- On Windows PowerShell, remember that bare `npm` may fail because `npm.ps1` is blocked; `npm.cmd` is the practical fallback.
- If a Vite/esbuild build fails with `spawn EPERM`, check process-spawn permissions before debugging the app itself.

## What's in Memory

### EcoWorld checkout

#### 2026-05-12

- Project-root cleanup and shared PHP asset cache busting: EcoWorld, tmp, test-results, cdp-profile, layout-check.mjs, htmlHead.php, htmlBody.php, init.php, ECO_ASSET_VERSION, php -l
  - desc: Covers EcoWorld project-root maintenance in `cwd=\\?\C:\Users\user\Desktop\ecoworld`, including deleting disposable `_reference`, `tmp`, and `test-results` content after checking references, plus adding second-precision PHP cache busting for shared CSS/JS includes. Search this first for EcoWorld cleanup requests, stale asset reload complaints, or shared PHP layout asset handling.
  - learnings: `test-results/layout-check.mjs` was referenced in `BLUEPRINT.md`, so reference checks mattered before deleting the whole QA folder. The validated shared asset pattern was `ECO_ASSET_VERSION = date('YmdHis')` in `lib/init.php`, then versioned links in `lib/htmlHead.php` and `lib/htmlBody.php`, verified with `php -l`.

- `.gemini` routing hydration for EcoWorld website context: ai read .gemini knowledge, EcoWorld, ECOWORLD_IMPLEMENTED_UI_NOTES_2026-05-12.md, GEMINI_DYNAMIC_ROUTING.md, Update-GeminiRouting.ps1, ROUTER.idx, ATLAS.idx
  - desc: Covers the successful `ai read .gemini knowledge` hydration flow in `cwd=\\?\C:\Users\user\Desktop\ecoworld`, including the bridge read order, router refresh, fallback indexes/kernels, and loading the active EcoWorld UI note. Search this first for EcoWorld tasks that need `.gemini` context loaded quickly without broad tree reads.
  - learnings: The validated path is `00_CODEX_START_HERE.md` -> `GEMINI_FULL_ACCESS_ROUTING.md` -> router refresh -> `GEMINI_DYNAMIC_ROUTING.md` -> `route.yaml` -> fallback indexes/kernels as needed. The active retrieval handle was `ECOWORLD_IMPLEMENTED_UI_NOTES_2026-05-12.md`.

#### 2026-05-11

- Free visual asset fallback and skill updates: EcoWorld, FREE_VISUAL_ASSET_SOURCING.md, free-visual-assets, Unsplash, Pexels, Pixabay, Material Symbols, SVG, CSS art
  - desc: Covers the reusable "no image-generation tool available" workflow built around EcoWorld image requests, including the shared Gemini fallback file, the native Codex `free-visual-assets` skill, and blueprint-level guidance for sourcing, caching, and documenting visuals. Search this first for `cwd=\\?\C:\Users\user\Desktop\ecoworld` tasks that need non-paid imagery, asset sourcing policy, or persisted image workflow updates.
  - learnings: The durable path here is project-owned assets first, then free stock sources, then icons/SVG/CSS art, then local caching and source notes. The user wanted this stored in skills/knowledge, not left as a one-off answer.

- Homepage filter/search modernisation: EcoWorld, filter panel, information.txt, chip scroller, scrollbar, lib/components.php, css/style.css, filter-selects, masonry layout
  - desc: Covers the EcoWorld homepage filter-panel redesign grounded in the live EcoWorld white/green brand reference, including the component/CSS touchpoints and the final scrollbar-hiding request. Search this first for `cwd=\\?\C:\Users\user\Desktop\ecoworld` tasks involving homepage controls, chips, select styling, or brand-matched UI cleanup.
  - learnings: The validated path was to read `information.txt` and the real site before styling, then patch the live `style.css` block exactly. Keep horizontal chip scrolling, but hide the scrollbar UI rather than disabling overflow.

### Windows Codex home / `.gemini` bridge

#### 2026-05-04

- Codex `.gemini` full access routing and auto-refresh: .gemini, .codex, GEMINI_FULL_ACCESS_ROUTING.md, GEMINI_DYNAMIC_ROUTING.md, ROUTER.idx, ATLAS.idx, Update-GeminiRouting.ps1, SESSION_SHADOW.json
  - desc: Covers building a Codex-side bridge so the assistant can understand and reuse `.gemini` knowledge, memory, and skills, plus a manifest-based dynamic router and watcher that refreshes Codex-owned routing artifacts when safe `.gemini` files change. Search this first for tasks in `cwd=\\?\C:\Users\user\Documents\Codex\2026-05-04\ai-add-a-codex-shortcut-at` or Windows Codex-home work that needs folder relationship mapping, `.gemini` read order, skill conversion boundaries, or refresh automation.
  - learnings: The durable route starts with the Codex bridge and `.gemini` indexes, not a full-tree read. `route.yaml` pointed to a missing `antigravity\route.yaml`, so the validated fallback was `GEMINI.md`, `ROUTER.idx`, `ATLAS.idx`, kernel files, and `skill_path_router.md`. For automation, manifest/hash comparison plus a user-level Startup watcher worked when `schtasks` did not.

### Older Memory Topics

#### quizLAA repo family

- Vue app Supabase wiring aligned to admin-panel pattern and production build: admin-panel-quizLaa, webApp-LAA-quiz-v2, development.localhost, development.supabase, vite.loadEnv, npm.cmd, spawn EPERM
  - desc: Covers comparing `webApp-LAA-quiz-v2` against `admin-panel-quizLaa`, mirroring the admin panel's explicit Vite mode/env contract, and then running a successful production build. Use this for `cwd=\\?\C:\Users\user\Desktop\quizLAA` / `c:\Users\user\Desktop\quizLAA\webApp-LAA-quiz-v2` when tasks involve Supabase URLs, Vite mode naming, `.env` layout, or Windows build execution.
