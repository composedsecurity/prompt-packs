---
title: "Find frontend-only access controls"
slug: "audit-frontend-only-authz"
category: "authentication"
type: "prompt"
tags: ["auth", "authorization", "audit"]
source: "https://composedsecurity.com/blog/10-security-prompts-for-vibe-coders"
source_label: "Prompt 9"
---

# Find frontend-only access controls

Locate client-side authorization checks and generate the backend or RLS enforcement to back them.

> Part of the **Authentication & Access Control** pack. From the Composed Security blog: [10 Copy-Paste Security Prompts for Your AI Agent](https://composedsecurity.com/blog/10-security-prompts-for-vibe-coders).

## Prompt

```text
Audit this app for authorization that happens only in the frontend. Frontend checks are bypassable in 5 seconds with browser DevTools. All are critical. Read-only.

Step 1: find every authorization check. Search for: `isAdmin`, `isOwner`, `hasRole`, `can*`, `role ===`, `permissions.includes`. `if (user.role)`, `if (user.tier)`, `if (user.subscription)`. Conditional rendering of admin UI / paid features / sensitive actions. Custom hooks: `useIsAdmin`, `useCanEdit`, `usePermission`. Route guards / HOCs / layout-level checks. For each: file:line, the check expression, what it gates.

Step 2: classify each. FRONTEND_ONLY: only browser-side; backend doesn't enforce. BACKEND_ONLY: backend enforces; no frontend check (fine but maybe poor UX). DEFENSE_IN_DEPTH: both (ideal).

Step 3: for every FRONTEND_ONLY, find the corresponding API route or DB query. Generate backend enforcement. Pick: (A) API route check: verify session server-side; read role/permissions from DB OR verified session token (NOT request body); return 403 if check fails BEFORE doing work. (B) Database RLS: for DB read/write, write or extend RLS policy enforcing the rule at DB level. Most robust: rule applies even if accessed via other paths. (C) Middleware: Next.js `middleware.ts` gating route segments. Generate matcher + role check.

Step 4: output as markdown table. File:Line, Frontend Check, Gates, Current Backend Status, Proposed Backend Fix, Code.

KEEP frontend checks (good UX). Just ensure backend enforces every one. CRITICAL flags: user_id/owner_id/tenant_id used in check coming from URL or request body, not session (horizontal privilege escalation); admin endpoint accepting `userId` parameter (verify restricted to actual admins, not any authenticated user). Do NOT modify code. Output audit + proposed fixes for my approval.
```

## How to use

Paste the block above into your coding agent (Cursor, Claude Code, Codex, Lovable, or Bolt). Give it read access to the repo. Keep it read-only where the prompt says so, and verify each finding before acting on it.

---

Found this useful? [Composed Security](https://composedsecurity.com) reviews your pull requests for exactly this class of bug.
