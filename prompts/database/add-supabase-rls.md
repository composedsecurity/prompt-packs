---
title: "Add Row Level Security to every Supabase table"
slug: "add-supabase-rls"
category: "database"
type: "prompt"
tags: ["supabase", "rls", "authorization"]
source: "https://composedsecurity.com/blog/10-security-prompts-for-vibe-coders"
source_label: "Prompt 2"
---

# Add Row Level Security to every Supabase table

Inventory, classify, and generate RLS policies safely, without locking users out.

> Part of the **Database** pack. From the Composed Security blog: [10 Copy-Paste Security Prompts for Your AI Agent](https://composedsecurity.com/blog/10-security-prompts-for-vibe-coders).

## Prompt

```text
Add Row Level Security to every Supabase table. Wrong policies can lock users out. Follow this exact procedure.

Step 1: inventory tables in `public` schema. Use Supabase MCP if available, else read migrations/SQL files. Output: Table, Has user_id-style FK?, RLS enabled?, Existing policies.

Step 2: classify each table. USER_OWNED: column ties row to auth.users (user_id, owner_id, profile_id, created_by). PUBLIC_REF: shared reference data (countries, products catalog). TENANT_OWNED: has tenant_id/org_id/workspace_id. ADMIN_ONLY: never client-accessible (audit logs, system config). AMBIGUOUS: STOP. Ask before generating policies.

Step 3: for non-ambiguous tables, generate SQL. `ALTER TABLE ... ENABLE ROW LEVEL SECURITY`. USER_OWNED: SELECT `auth.uid() = user_id`; INSERT `with check (auth.uid() = user_id)`; UPDATE `auth.uid() = user_id with check (auth.uid() = user_id)`; DELETE `auth.uid() = user_id`. PUBLIC_REF: SELECT `to authenticated, true`; writes have no public policy (service role only). TENANT_OWNED: use helper `is_member_of(tenant_id uuid)` checking memberships table; generate it if missing; all CRUD use is_member_of(tenant_id). ADMIN_ONLY: no policies for anon/authenticated; document server-side service role only.

Step 4: write migration to `supabase/migrations/<timestamp>_enable_rls.sql`. Do NOT execute.

Step 5: for each table, generate ONE example query that should succeed and ONE that should fail. Output as markdown checklist for post-migration verification.

Step 6: final summary. Tables RLS-enabled: N. Policies created: M. AMBIGUOUS tables needing my decision: list each. Tables with existing policies: do NOT overwrite; output diff for my review.

Hard rules. Never disable an existing policy without explicit confirmation. Never `USING (true)` on USER_OWNED or TENANT_OWNED. That grants global read. No obvious user_id FK = AMBIGUOUS. Don't guess.
```

## How to use

Paste the block above into your coding agent (Cursor, Claude Code, Codex, Lovable, or Bolt). Give it read access to the repo. Keep it read-only where the prompt says so, and verify each finding before acting on it.

---

Found this useful? [Composed Security](https://composedsecurity.com) reviews your pull requests for exactly this class of bug.
