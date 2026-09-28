---
title: "Audit MCP servers for command execution"
slug: "audit-mcp-stdio-rce"
category: "supply-chain"
type: "prompt"
tags: ["mcp", "rce", "agentic-security"]
source: "https://composedsecurity.com/blog/mcp-stdio-rce"
source_label: "Hand to your agent"
---

# Audit MCP servers for command execution

Inventory MCP servers, flag public binds and untrusted-input command influence, and check SDK versions against known CVEs.

> Part of the **Supply Chain & Incident Response** pack. From the Composed Security blog: [Your MCP server is a shell. Anthropic calls it expected.](https://composedsecurity.com/blog/mcp-stdio-rce).

## Prompt

```text
You are a security reviewer auditing my repo and local agent setup for the 2026 MCP STDIO command-execution class (OX Security disclosure; CVE-2026-33032, CVE-2026-30623, CVE-2026-30615, CVE-2025-54136, CVE-2026-22252, CVE-2025-49596). Report findings with file paths and line numbers.

1. Find every MCP server config (~/.claude/settings.json, .cursor/, .vscode/mcp.json, any *.mcp.json, docker-compose, k8s manifests). List each server, its transport (stdio or http), and whether it binds to anything other than localhost.

2. Flag any MCP server reachable on a public interface (0.0.0.0 or a routable host) as critical.

3. Flag any server whose command, args, or env can be influenced by untrusted input (PR titles, issue bodies, web fetches, marketplace descriptors, other agents).

4. List SDK and client versions (mcp Python, TypeScript, Java, Rust, plus LiteLLM, Cursor, LibreChat, Windsurf, Flowise) and check each against the known-vulnerable versions for the CVEs above.

5. Identify any tool that performs a destructive action (shell, file write, deploy, db write) without a human-in-the-loop gate.

6. Output a prioritized fix list: pin or patch, bind to localhost, sandbox, allowlist tools, add approval gates, revoke any credential a vulnerable server could read.

Do not execute fixes. Report only.
```

## How to use

Paste the block above into your coding agent (Cursor, Claude Code, Codex, Lovable, or Bolt). Give it read access to the repo. Keep it read-only where the prompt says so, and verify each finding before acting on it.

---

Found this useful? [Composed Security](https://composedsecurity.com) reviews your pull requests for exactly this class of bug.
