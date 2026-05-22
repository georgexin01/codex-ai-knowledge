# Reusable Vben Admin + Supabase database planning principles

Scope: Reusable cross-project guidance for Codex and Claude-style workflows when planning a new Vben Admin + Supabase database and writing `DATABASE.md`, migrations, auth/RLS helpers, and project schema tables.

Use this as a general reference. Keep project-specific details in separate project notes.

## 1. Minimum database planning contract

Do not plan only content tables.
For a Vben Admin + Supabase project, the planning pass must explicitly check these layers:

1. `public.project`
- project registry row
- dedicated `project_id`
- dedicated `schema_name`

2. `public.role`
- project-scoped role definitions
- include permission level ordering if the stack uses role levels

3. `public.permission`
- canonical resource/action/scope registry

4. `public.role_permission`
- role-to-permission mapping

5. `public.user`
- shared auth bridge between `auth.users` and project membership
- needed for project isolation and JWT-based access control

6. `{schema}.users`
- business/admin users table used by the admin panel UI and profile fetch paths
- do not assume `public.user` alone is enough

7. `{schema}.permissions`
- business-schema permission matrix if project-local helper functions or frontend flows expect schema-level permission rows

8. `{schema}.attachments`
- required whenever upload flows or attachment album/media flows query `.from('attachments')`

## 2. Authorization contract

Always verify and document:
- project isolation by dedicated `project_id`
- project-specific roles
- project-specific permissions
- project-specific storage bucket if storage is used
- JWT app claims such as:
  - `user_role`
  - `project_id`
  - `role_level`
- do not overload reserved Supabase JWT claim `role` for app RBAC
- RLS must be enabled on every exposed business table
- helper functions such as `{schema}.authorize()` and `{schema}.get_permission_scope()` must read from the actual permission source used by the project

## 3. Double-binding auth principle

This project family usually needs all three layers aligned:
- `auth.users`
- `public.user`
- `{schema}.users`

Meaning:
- `auth.users` = login account
- `public.user` = project binding + role binding
- `{schema}.users` = business/admin profile used by the panel

If any one is missing, login, profile fetch, or user management may fail.

## 4. Trigger and casing principle

Before creating business tables, inspect naming style.
If business tables use camelCase columns like `createdAt`, `updatedAt`, `isDelete`, do not reuse snake_case trigger helpers blindly.

Check for:
- snake_case trigger helper for `updated_at`
- camelCase trigger helper for `updatedAt`

## 5. Attachments principle

If code contains any of these patterns, attachments are a must-check item:
- `stores/attachments.ts`
- `utils/upload.ts`
- `.from('attachments')`
- `safe_delete_active_attachment`

Then planning must include:
- `{schema}.attachments`
- attachment permission rows
- attachment RLS policies
- storage bucket verification
- safe-delete RPC if expected by code

## 6. DATABASE.md generation rule

When generating or updating `DATABASE.md`:
- include auth bridge tables, permission layers, business users, and attachments if upload flows exist
- do not list only content tables
- explicitly mark storage bucket and isolation contract
- explicitly mark which modules are active, deferred, or legacy leftovers

## 7. Pre-implementation verification checklist

Before declaring the plan complete, check:
- does active code query `.from('users')`?
- does it query `.from('permissions')`?
- does it query `.from('attachments')`?
- does it call schema RPCs like `create_user`, `update_user`, `delete_user`, `restore_user`?
- does it rely on `{schema}.authorize()` or `{schema}.get_permission_scope()`?
- does upload code require attachment metadata rows and a storage bucket?

If yes, these must be present in the schema plan and migration set.

## 8. Recommended implementation order

1. public auth/RBAC foundation
2. project schema core helpers
3. simple business/content tables
4. role and permission seeds
5. RLS helpers and table policies
6. business `users`
7. business `permissions`
8. business `attachments`
9. first admin login user
10. cleanup of legacy modules/routes not included in current phase

## 9. Reuse boundary

This note is reusable across similar Vben Admin + Supabase projects.
Do not put project-specific ids, URLs, or active-folder authority rules here. Keep those in separate project notes.
