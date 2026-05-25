---
name: skill-path-router
description: "Canonical skill path index — maps trigger phrases to exact SKILL.md entry points. Read this before scanning skill directories."
triggers: ["skill path router", "skill_path_router", "ai read .codex skills", "which skill", "what skill"]
version: 2.0
date_updated: "2026-05-21"
status: authoritative
---

# SKILL PATH ROUTER V2.0

## How to use
1. Match the user trigger phrase against the table below.
2. Read ONLY the matched SKILL.md — do not scan the full skill tree.
3. If no match: fall back to `skills/` directory listing, then grep `description:` from frontmatter.

## Trigger → Entry Point Map

| Trigger | Entry Point | What it covers |
|---|---|---|
| `ai claude` | `skills/claude/WORKING_PROGRESS.md` | Vben Admin module builder — 41 linear micro-tasks (handshake → build → publish). Code vault: `create-module/skill.md` |
| `ai claude app` | `skills/claude-app/WORKING_PROGRESS.md` | Mobile app Vue builder — 38 linear micro-tasks (handshake → foundation → data → UI → deploy). Consumes design/app DESIGN.md |
| `ai claude website` | `skills/claude-website/WORKING_PROGRESS.md` | PHP + Supabase REST builder — 45 linear micro-tasks (handshake → foundation → engine → endpoints → publish) |
| DB handshake (shared) | `skills/SHARED_DB_CONTRACT.md` | Contract for the 3 builders above — schema, bucket, project_id, env matrix, schema-ownership rule |
| `ai claude meta` | `skills/claude-meta/SKILL.md` | Claude meta-skills and self-improvement patterns |
| `ai design app` | `skills/design/app/SKILL.md` | Mobile app design execution (9-step build: scaffold → DESIGN.md → tokens → views → verify) |
| `ai design website` | `skills/design/website/SKILL.md` | Website design execution (13-step: inventory → cinematics → components → SEO → handover) |
| `ai design spec` | `skills/design/_spec/SKILL.md` | DESIGN.md contract layer (lint rules, export guide, Tailwind/DTCG export, examples) |
| `ai karpathy` | `skills/karpathy-guidelines/SKILL.md` | Karpathy coding quality rules (surgical scope, simplicity, verification) |
| `ai imagegen` | `skills/imagegen/SKILL.md` | Image generation workflows and free-asset fallback |
| `ai markdown mindmap` | `skills/markdown-database-mindmap/SKILL.md` | Database schema → Markmap visualization |
| `ai project handoff` | `skills/project-handoff-doc-stack/SKILL.md` | Root handoff docs (AI_COLLAB_PROJECT_OS, MASTER_PLAN, DATABASE, CROSSWALK) |

## Recipe & Knowledge triggers (memories/)

These point at executable recipes and foundational knowledge docs, not skills.

| Trigger | Entry Point | What it covers |
|---|---|---|
| `ai recipe blueprint` | `memories/CLAUDE_BLUEPRINT_RECIPE.md` | Generate BLUEPRINT.md / DESIGN.md for a new project (Tier-2, required by other recipes) |
| `ai recipe mobile app` | `memories/MOBILE_APP_DESIGN_RECIPE.md` | Canonical clone-template for the user's preferred mobile aesthetic |
| `ai recipe image to app` | `memories/IMAGE_TO_MOBILE_APP_PIPELINE.md` | Convert design image folders → Vue mobile app (23+ canonical pages) |
| `ai recipe header footer` | `memories/1_core/HEADER_FOOTER_DESIGN_RULES.md` | MUST-FOLLOW header + bottom-nav rules for mobile apps |
| `ai recipe free images` | `memories/1_core/IMAGE_SOURCING_FREE.md` | Free image waterfall: Pollinations → Unsplash → Lorem Picsum → icons → SVG/CSS |
| `ai recipe pwa` | `memories/1_core/PWA_FAVICON_META_SETUP.md` | PWA + favicon + OG/Twitter Card + Apple/Microsoft meta setup |
| `ai design sop` | `memories/1_core/DESIGN_SOP.md` | Page-level structural manifest (Transactional / Operations / Glass blueprints) |
| `ai design evolution` | `memories/1_core/DESIGN_EVOLUTION_PROTOCOL.md` | Framework for AI to evolve design senses from user feedback |
| `ai user dna` | `memories/0_apex/USER_DNA.md` | Tier-0 user taste profile (Trusta Industrial) — required by all design recipes |
| `ai gitnexus` | `memories/2_governance/GITNEXUS.md` | GitNexus MCP code-graph workflow + project allowlist |
| `ai drift guard` | `memories/2_governance/DRIFT_GUARD_PROTOCOL.md` | Anti-drift re-grounding protocol for long tasks |
| `ai knowledge rot` | `memories/2_governance/KNOWLEDGE_ROT_PROTOCOL.md` | Anti-entropy governance (MEMORY.md auto-trim + tombstone rule) |

## Sub-skill index (no top-level SKILL.md — load sub directly)

### skills/claude/ sub-skills
| Sub-skill | Path |
|---|---|
| Full module (end-to-end) | `skills/claude/create-module/skill.md` |
| Schema analysis | `skills/claude/analyze-schema/skill.md` |
| Pinia store + CRUD | `skills/claude/generate-store/skill.md` |
| Supabase SQL + RLS | `skills/claude/generate-supabase-schema/skill.md` |
| Vue views + drawers | `skills/claude/generate-views/skill.md` |
| Vue Router module | `skills/claude/generate-route/skill.md` |
| i18n (zh-CN/en-US) | `skills/claude/generate-i18n/skill.md` |
| Image upload + crop | `skills/claude/image-upload-spec/skill.md` |
| E2E tests | `skills/claude/generate-e2e/skill.md` |
| Workflow tests | `skills/claude/workflow-test/skill.md` |
| Supabase auth arch | `skills/claude/supabase-auth-architecture/skill.md` |
| RLS + RBAC design | `skills/claude/supabase-rls-rbac-design.md` |
| MCP Supabase conn | `skills/claude/mcp-supabase-postgres-connection.md` |
| Local Docker lessons | `skills/claude/VBEN_SUPABASE_LOCAL_LESSONS.md` |

### skills/design/ sub-skills
| Sub-skill | Path |
|---|---|
| App spec examples | `skills/design/_spec/examples/atmospheric-glass/` |
| Website step 4 | `skills/design/website/04-php-modularization/skill.md` |
| Website step 5 | `skills/design/website/05-hero-cinematics/skill.md` |
| Website step 6 | `skills/design/website/06-component-engineering/skill.md` |

## System skills (internal — not user-triggered)
- `skills/.system/skill-installer/SKILL.md` — install skills from GitHub
- `skills/.system/skill-creator/SKILL.md` — create new skill packages
- `skills/.system/plugin-creator/SKILL.md` — create OpenAI plugins
- `skills/.system/openai-docs/SKILL.md` — OpenAI API reference

## Excluded from routing
- `skills/faucet/` — excluded per router-config.json (security boundary)
- `skills/normal/` — reference library only, no direct triggers
