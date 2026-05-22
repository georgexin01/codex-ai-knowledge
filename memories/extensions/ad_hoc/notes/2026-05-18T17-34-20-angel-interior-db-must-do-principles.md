# Angel Interior database must-do principles

Scope: Future Codex or Claude-style work for Angel Interior and similar Vben Admin + Supabase multi-project setups.
Reason: Prevent missing core business tables and auth/RBAC layers during database planning, `DATABASE.md` authoring, and migration creation.

## 1. Must-not-miss core pattern

When creating a new project-scoped Supabase database for a Vben admin project, do NOT stop at content tables.
The minimum required contract must check and usually include all of these layers:

1. `public.project`
- dedicated project row
- dedicated `project_id`
- dedicated `schema_name`
- must not reuse another project's runtime scope by accident

2. `public.role`
- project-scoped role definitions
- explicit `level`
- explicit active/inactive and delete flags if existing stack uses them

3. `public.permission`
- canonical permission registry for `resource + action + scope`

4. `public.role_permission`
- role-to-permission mapping
- needed before business-schema authorization functions can work correctly

5. `public.user`
- auth bridge table
- binds `auth.users` to a specific project and role
- required for project isolation and JWT claim flow

6. `{schema}.users`
- business/admin users table shown in project schema
- separate from `public.user`
- current Vben auth/store patterns often query this table directly
- if missing, Studio under project schema looks incomplete and login/profile fetch can fail

7. `{schema}.permissions`
- business-schema permission matrix
- often required by project-local `authorize()` and `get_permission_scope()` helpers
- do not assume `public.permission` alone is enough if the frontend/backend pattern expects schema-level permission rows

8. `{schema}.attachments`
- if current Vben admin has upload utilities or album/media stores using `.from('attachments')`, this table is a must-check item
- include permission rows and RLS for attachments too
- also check for any safe-delete RPC expected by upload utilities

## 2. Authorization and rules principles

When writing `DATABASE.md` or planning migrations, always verify and document these authorization layers:

- project isolation by dedicated `project_id`
- project-specific roles only
- project-specific permissions only
- project-specific storage bucket if storage is used
- project-scoped JWT claims such as:
  - `user_role`
  - `project_id`
  - `role_level`
- do NOT overload reserved Supabase JWT claim `role` for app RBAC
- RLS must be enabled on every exposed business table
- helper functions like `{schema}.authorize()` and `{schema}.get_permission_scope()` must be checked against actual permission storage location

## 3. Business-table double-binding principle

For this Vben/Supabase family, login and admin access are usually a double-binding system:

1. `auth.users`
- authentication account

2. `public.user`
- project binding and role binding

3. `{schema}.users`
- business/admin profile used by the panel

If any one of these is missing or not synchronized, login or admin user management can break.

## 4. Trigger and casing principle

Before creating new schema business tables, verify naming style.
If business tables use camelCase columns like `createdAt`, `updatedAt`, `isDelete`, do not reuse snake_case trigger helpers blindly.

Must check:
- trigger function for snake_case tables, e.g. `updated_at`
- separate trigger function for camelCase tables, e.g. `updatedAt`

Missing this causes silent update failures or broken trigger behavior.

## 5. Attachments module principle

If the active admin panel contains any of these patterns, attachments are not optional:
- `stores/attachments.ts`
- `utils/upload.ts`
- `.from('attachments')`
- `safe_delete_active_attachment`

In that case, database planning must include:
- `{schema}.attachments`
- attachment permission seeds
- attachment RLS policies
- storage bucket verification
- safe-delete RPC if current code expects it

## 6. Angel Interior-specific latest state

Active target:
- `admin-panel-angel` = current Angel project admin panel

Reference only:
- `admin-panel-trash` = old history/reference only
- may copy patterns from Trash into Angel, but do not edit Trash project behavior/state

Local runtime:
- Supabase Studio: `http://localhost:54323`
- local Docker Supabase only

Angel project contract:
- schema: `angel`
- project key: `angel-interior`
- project id: `b3e45339-0de0-4073-b03a-7f5468bffe77`
- storage bucket: `angel-interior`

Angel database currently must include at minimum:
- `public.project`
- `public.role`
- `public.permission`
- `public.role_permission`
- `public.user`
- `angel.users`
- `angel.permissions`
- `angel.attachments`
- `angel.media_assets`
- `angel.blog_categories`
- `angel.blog_posts`
- `angel.sketchup_categories`
- `angel.sketchup_resources`
- `angel.material_categories`
- `angel.material_resources`
- `angel.contact_submissions`

## 7. DATABASE.md generation rule

When generating or updating `DATABASE.md` for Vben admin + Supabase projects:
- do not only list content tables
- explicitly include auth bridge tables, permission layers, business user table, and upload/attachment table if used by code
- explicitly mark storage bucket and project isolation contract
- explicitly mark whether old modules are active, deferred, or legacy leftovers
- explicitly note if reference projects are read-only reference only

## 8. Pre-implementation verification checklist

Before declaring the database plan complete, always check:
- does the active frontend query `.from('users')`?
- does it query `.from('permissions')`?
- does it query `.from('attachments')`?
- does it call schema RPCs like `create_user`, `update_user`, `delete_user`, `restore_user`?
- does it rely on `authorize()` or `get_permission_scope()`?
- does upload code require a storage bucket and attachment metadata rows?

If yes, those tables/functions must be present in the plan and migration set.

## 9. Angel workflow sequencing principle

Recommended order for this project family:
1. public auth/RBAC foundation
2. project schema core helpers
3. simple content tables
4. permission seeds and role mappings
5. RLS helpers and policies
6. business `users`
7. business `permissions`
8. business `attachments`
9. first admin login user
10. route/module cleanup for legacy modules not part of current phase

## 10. Status note

This note was added after Angel Interior initially missed `angel.users`, `angel.permissions`, and `angel.attachments`, even though the active panel code expected them.
Treat this as a must-do safeguard for future database planning and skill-guided implementation.
