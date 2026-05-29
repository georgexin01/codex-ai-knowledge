thread_id: 019e6dd9-0d7a-7281-ad36-a6163c86d01b
updated_at: 2026-05-28T09:13:18+00:00
rollout_path: C:\Users\user\.codex\sessions\2026\05\28\rollout-2026-05-28T17-10-01-019e6dd9-0d7a-7281-ad36-a6163c86d01b.jsonl
cwd: \\?\C:\Users\user\Documents\restore-local

# restore-local Supabase recovery toolkit was mapped and documented into a new root README.

Rollout context: The user asked for an AI-friendly explanation of the `restore-local` folder, including what it does, its workflow step by step, and a saved `readme.md`/`README.md` for future AI updates. The assistant first loaded the `.codex` knowledge route because the user explicitly requested it, then inspected the folder contents and the restore/backup scripts, and finally wrote `README.md` at the repo root.

## Task 1: Read .codex knowledge first, then inspect restore-local

Outcome: success

Preference signals:

- The user said: "ai read .codex knowledge first then do above request in chat." -> in similar situations, start by hydrating the local Codex routing/knowledge layer before working in the project folder.

Key steps:

- Read `C:\Users\user\.codex\00_CODEX_START_HERE.md`, then `CODEX_FULL_ACCESS_ROUTING.md`, then `CODEX_DYNAMIC_ROUTING.md` to resolve the route-first workflow.
- Returned the expected sentinel response `[🟢] Agent is Ready..` after route hydration.
- Inspected `restore-local` contents with `Get-ChildItem -Force` and `rg --files`.

Reusable knowledge:

- The Codex router docs explicitly say to use route-first selective loading and to stop after the first valid route match.
- This rollout confirmed the `restore-local` workspace is primarily a Supabase backup/restore operations folder rather than an application source tree.

References:

- [1] `Get-Content C:\Users\user\.codex\00_CODEX_START_HERE.md`
- [2] `Get-Content C:\Users\user\.codex\CODEX_DYNAMIC_ROUTING.md`
- [3] `Get-ChildItem -Force` in `C:\Users\user\Documents\restore-local`
- [4] `rg --files` output showed the root scripts plus `restore-single\...` snapshot files

## Task 2: Analyze restore-local and write README.md

Outcome: success

Preference signals:

- The user asked to "study this folder", understand "what they do and know what they are", explain the flow "step by step", and "write down every information ai get from here the root restore-local and save in a new files call readme.md" -> future similar tasks should produce a root-level AI orientation file, not just a terse summary.
- The user also said the `.md` is for AI to "quickly understanding this restore-local folder and its information" and to keep "status or step for future updates here" -> future similar docs should include a living status/update section.

Key steps:

- Read the main scripts: `backup-local.bat`, `restore-local.bat`, `restore-single.bat`, `restore-trash.bat`, `reset & restore-supabase.bat`, `extract_angelInterior.ps1`, `extract_quizlaa.ps1`, `extract_quizlaa.py`, and `vps comand.txt`.
- Inspected the packaged snapshot under `restore-single\trash-20260522-140801\trash-20260522-140801` and its `manifest.json`.
- Read representative edge-function and SQL contents to infer the restore bundle shape.
- Wrote `README.md` at the repo root and verified it by reading it back.

Reusable knowledge:

- `backup-local.bat` creates a timestamped backup folder under `C:\Users\user\Documents\supabase-backup-restore` and captures SQL dumps, auth data, storage metadata, grants, zipped storage files, zipped edge functions, and `.env`.
- `restore-local.bat` performs a full local restore by dropping custom schemas, clearing auth/storage metadata, restoring the SQL dumps, reapplying grants, restoring storage/functions, restarting containers, and verifying counts.
- `restore-single.bat` is the safer project-level restore path: it reads `manifest.json`, restores only the selected schema/project, and keeps other schemas/projects untouched.
- `reset & restore-supabase.bat` is the VPS sync controller with three modes: full restore VPS→local, pull one schema VPS→local, push one schema local→VPS.
- The packaged snapshot currently present is for project `Trash` / schema `trash`, with manifest row counts for schema tables, `public` rows, `auth.users`, and storage objects.
- The root contains a small `supabase/` metadata folder only (`.branches/_current_branch`, `.temp/cli-latest`), not a full app tree.

Failures and how to do differently:

- `restore-trash.bat` appears path-stale: it points to `C:\Users\user\Documents\restore-local\trash-20260522-140801\trash-20260522-140801`, but the actual snapshot found is under `restore-single\trash-20260522-140801\trash-20260522-140801`.
- The scripts use inconsistent hardcoded base paths (`install-supabase\supabase\docker` vs `local-supabase\supabase`), so future runs should check and normalize paths before execution.
- The root also contains a scratch file `p%` with secret-like values; it should be treated as sensitive and excluded from any future documentation or summaries.

References:

- [1] `backup-local.bat` dump flow includes `backup_full.sql`, `backup_schema.sql`, `backup_custom.sql`, `backup_auth.sql`, `backup_storage_meta.sql`, `backup_grants.sql`, `storage.zip`, `edge_functions.zip`, and `backup.env`
- [2] `restore-single\trash-20260522-140801\trash-20260522-140801\manifest.json` with `schema: trash`, `projectId: fddcc8d4-2f70-4cdc-b5a4-b2fee7b9d8f6`, `projectName: Trash`
- [3] `README.md` created at `c:\Users\user\Documents\restore-local\README.md`
- [4] `restore-trash.bat` hardcoded backup path mismatch noted above
- [5] `p%` identified as sensitive scratch material and intentionally not reproduced in the README

