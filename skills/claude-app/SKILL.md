---
name: claude-app
description: "V8.0 mobile app Vue builder — 13-step orchestrator for Vue 3 + Supabase + Capacitor mobile/PWA apps. Build-only: consumes the visual design from skills/design/app (DESIGN.md). Each step is a self-sufficient code vault (copy-paste ready)."
triggers: ["claude app", "claude-app", "mobile app build", "vue mobile app", "build mobile app", "new app module", "capacitor app", "pwa app build"]
phase: 0-orchestrator
version: 8.0
status: authoritative
last_updated: "2026-05-21"
---

# `claude-app` — Mobile App Vue Builder V8.0

> **Linear executor**: for step-by-step task execution use [`WORKING_PROGRESS.md`](WORKING_PROGRESS.md). This SKILL.md is the code-vault reference the linear file points into.
> **Design input**: visual design, tokens, and `DESIGN.md` come from [`../design/app/SKILL.md`](../design/app/SKILL.md). This skill builds the Vue code; it does not invent the design.

## 🎯 When to Use

Building or refactoring a Vue 3 + Supabase + Capacitor mobile/PWA app. Use this as the clinical orchestrator for the **13-Step Industrial App Lifecycle**.

This skill is **self-sufficient** — every step contains its own copy-paste Code Vault. The reference template `webApp-bakery-v2/` is no longer required.

## 🧭 Folder Anchors (the 6 pillars)

The webApp's `src/` layer has six load-bearing folders. Every step below anchors to one of them (plus foundational/deployment steps):

| `src/` Folder | Role | Owning Step |
|---|---|---|
| `src/api/` | Platform-aware HTTP + Supabase clients | **03** |
| `src/config/` | Single source of `import.meta.env.VITE_*` access | **02** |
| `src/types/` | TypeScript contracts used by stores + views | **05** |
| `src/stores/` | Pinia Bakery stores (most logic lives here) | **06** |
| `src/router/` | Dynamic + guarded routing | **10** |
| `src/views/` | Page components | **09** |

## 🚀 The 13-Step Industrial Protocol

### Phase 1 — Foundation (project plumbing)
1. **[01-handshake-genesis](01-handshake-genesis/skill.md)** — Project genesis: `package.json`, `vite.config.ts`, `tsconfig.json`, `index.html` (viewport=device-width), Pinia + router registration.
2. **[02-config-hardening](02-config-hardening/skill.md)** — `src/config/{env.ts, supabase.ts, index.ts}` — the only place `VITE_*` is read.
3. **[03-api-connectivity](03-api-connectivity/skill.md)** — `src/api/{apiClient.ts, capacitorClient.ts}` — platform-aware HTTP + Supabase wrapper.
4. **[04-auth-architecture](04-auth-architecture/skill.md)** — Supabase Auth, JWT extraction, fail-closed route guards, refresh-token flow.

### Phase 2 — Data Scaffolding (src/types + src/stores)
5. **[05-types-foundry](05-types-foundry/skill.md)** — `src/types/` — DB types, App types, request/response envelopes.
6. **[06-industrial-stores](06-industrial-stores/skill.md)** — `src/stores/` — Options-API Bakery pattern, identity filtering, `$reset` contract.
7. **[07-image-spec](07-image-spec/skill.md)** — Supabase Storage upload, `<AppImage>` fallback, Capacitor native image picker.

### Phase 3 — UI Foundry (src/views + styling)
8. **[08-ui-standardization](08-ui-standardization/skill.md)** — CSS variables, theme tokens, divider sections, EN UPPERCASE, contact-field pattern.
9. **[09-view-scaffolding](09-view-scaffolding/skill.md)** — `src/views/` — List / Detail / Form templates with loading + empty states.
10. **[10-routing-logic](10-routing-logic/skill.md)** — `src/router/index.ts` — guards, auto-import modules, redirect-to-login.
11. **[11-relational-sync](11-relational-sync/skill.md)** — M2M patterns, intersection filters, soft-delete, AnswerSnapshot-style history.

### Phase 4 — Locale + Native + Deploy
12. **[12-i18n-composables](12-i18n-composables/skill.md)** — vue-i18n auto-glob, `src/composables/` (Capacitor Clipboard/Share patterns).
13. **[13-native-pwa-deploy](13-native-pwa-deploy/skill.md)** — `capacitor.config.ts`, `manifest.json`, PWA service worker, staging + production deploy.

## 📖 Reference Vaults

- **Cookbook**: `_cookbook.md` — reusable snippets (pagination, fail-closed guard, Bakery store template, soft-delete filter). Linked from multiple steps.
- **Master Rules**: [`MASTER_RULES.md`](../../knowledge/3_domains/claude/MASTER_RULES.md) — Rule #1 (Supabase schema isolation) is the law.
- **Apex Kernel**: [`GROUND_KERNEL.md`](../../knowledge/0_apex/GROUND_KERNEL.md)
- **Project Snapshot**: [`LAA_PROJECT_SNAPSHOT.md`](../../knowledge/3_domains/claude/LAA_PROJECT_SNAPSHOT.md)

## 🛠️ Mandatory Execution Rules

- **CLINICAL SEQUENCING** — execute 01 → 13 in order for a new webApp. For targeted edits, you may enter at the step that owns the folder you're touching (see Folder Anchors above), but you MUST re-verify the `requires:` chain in that step's frontmatter.
- **SCHEMA ISOLATION (Rule #1)** — every query reads from the project schema (`quizLaa` for quizLaa-family webApps). Only `auth.users` is permitted cross-schema.
- **IDENTITY FILTERING** — all data retrieval is filtered by the authoritative `userId` (from auth store) and `projectId` (from `VITE_PROJECT_ID`). This is enforced in the store layer, not views.
- **CASING SYNC** — use `COALESCE(auth.jwt()->>'project_id', auth.jwt()->>'projectId')` in any RLS you touch from this skill.
- **CONFIG FUNNEL** — `import.meta.env.VITE_*` is read in `src/config/` ONLY. Everywhere else uses `env.*` from the barrel.

## ✅ Verify the Orchestrator

- `claude-app/` contains exactly 13 numbered sub-directories (01 → 13) + `SKILL.md` + `WORKING_PROGRESS.md` + `_cookbook.md` + `README.md`.
- Every sub-directory contains a `skill.md` with version ≥ 2.0 frontmatter and a 📦 Code Vault section.
- `SKILL.md` links every sub-directory exactly once.
- Zero references to `C:\Users\user\.claude\skills\*` (deprecated mirror path).

---
**Protocol Status**: V8.0 Active | **Architect**: Claude-App | **Self-Sufficient**: Yes (consumes design/app DESIGN.md)

## Sort Drag Pattern

For Vben admin list pages that expose a sortable `sort` column, use the proven gap-based drag strategy from QuizLAA instead of reassigning 1, 2, 3 on every drag.

Rules:
- Enable row dragging with `rowConfig.drag = true`, `gridEvents.rowDragend`, and `dragSort: true` on the `No.` column.
- Store `sort` values with gaps using `SORT_GAP = 1000`.
- On create, assign `nextSort = max(sort) + SORT_GAP`.
- On drag:
  - first position => `Math.floor((nextRow.sort ?? SORT_GAP) / 2)`
  - last position => `(prevRow.sort ?? 0) + SORT_GAP`
  - between rows => `Math.floor((prevRow.sort + nextRow.sort) / 2)`
- If the midpoint collides with a neighbor, call `renormalizeSort()` to rewrite rows as `1000, 2000, 3000...`.
- Prefer lightweight `updateSort(id, sort)` for normal drags and reserve full renormalization for exhausted gaps.
- Keep the visible label as simple `Sort`.

This pattern keeps drag reorder stable, cheap, and close to the QuizLAA lesson-list reference.
