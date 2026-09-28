# Database

Row Level Security and data-access guardrails.

Most apps built with an AI coding agent ship with a database that a stranger can read end to end, because the anon key is public and no policy stops it. This pack is about making the data layer enforce ownership instead of trusting the client.

**1 prompt in this pack.** [Back to all packs](../README.md)

## Prompts in this pack

| Prompt | Type | What it does |
|---|---|---|
| [Add Row Level Security to every Supabase table](./add-supabase-rls.md) | prompt | Inventory, classify, and generate RLS policies safely, without locking users out. |

## How to use this pack

Run the RLS prompt against your schema before launch. It will stop and ask whenever a table's ownership model is ambiguous, which is the safe behavior. Never accept `USING (true)` on a user-owned table.

## From the blog

These prompts are explained in full in the posts below. The post is where you get the failure mode, the reasoning, and the edge cases; the prompt is what you run.

- [10 Copy-Paste Security Prompts for Your AI Agent](https://composedsecurity.com/blog/10-security-prompts-for-vibe-coders)

## Related

- [All prompt packs](../README.md)
- [Secrets & Env Vars](../secrets/README.md)
- [Authentication & Access Control](../authentication/README.md)
- [API Hardening](../api-hardening/README.md)
- [Release Gate](../release/README.md)
- [Prompt Injection & Agent Authorization](../prompt-injection/README.md)
- [Agent Runtime & Model Harnesses](../agent-runtime/README.md)
- [Supply Chain & Incident Response](../supply-chain/README.md)
- [Composed Security blog](https://composedsecurity.com/blog)
