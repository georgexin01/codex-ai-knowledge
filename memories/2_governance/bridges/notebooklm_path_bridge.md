---
name: notebooklm-path-bridge
description: "NotebookLM path intake and token-lean research workflow for Codex."
triggers: ["notebooklm", "notebooklm path", "ai notebooklm", "research notebook path", "notebook path research"]
phase: reference
model_hint: gpt-5.4-mini
version: 1.0
---

# NotebookLM Path Bridge

## Purpose
Use this bridge when the user provides NotebookLM URLs or notebook IDs and asks for research, synthesis, or extraction.

## Automatic Activation
- Auto-activate when any prompt contains `notebooklm.google.com/notebook/`.
- Auto-activate when prompt includes a clear NotebookLM notebook UUID even without full URL.
- This route is default for NotebookLM-linked research tasks; users do not need to type `ai notebooklm`.

## Path Intake Contract
1. Accept URL format: `https://notebooklm.google.com/notebook/<id>`.
2. Extract notebook IDs and deduplicate them before analysis.
3. Track user-provided notebook links in `memories/2_governance/artifacts/notebooklm_registry.md`.

## Access Constraint
- Runtime may not be able to read private/authenticated NotebookLM pages directly.
- If direct access fails, request one of these handoff formats:
  - notebook summary
  - source list
  - exported FAQ/briefing
  - pasted excerpts
  - transcript text.

## Token-Optimized Research Flow
1. Route-first: read this bridge and `memories/2_governance/LIBRARY_INTELLIGENCE_PROTOCOL.md`.
2. Ingest only mission-relevant excerpts, not full raw notebook dumps.
3. Synthesize into high-density claims with uncertainty notes.
4. Persist short-lived task memory in `libraries/codex-migrated/memory/SESSION_SHADOW.json` only when needed.
5. Stop early once evidence is sufficient for the user task.

## Media Hygiene
- Transcript-first for video sources.
- No live-watch browsing unless explicitly requested.

## Deep Mode
When prompt includes deep/thorough/review:
- expand coverage and contradiction checks,
- include source-to-claim mapping,
- record unresolved questions explicitly.
