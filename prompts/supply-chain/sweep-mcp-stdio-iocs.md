---
title: "Sweep for MCP STDIO command execution"
slug: "sweep-mcp-stdio-iocs"
category: "supply-chain"
type: "command"
tags: ["mcp", "detection"]
source: "https://composedsecurity.com/blog/mcp-stdio-rce"
source_label: "First pass"
---

# Sweep for MCP STDIO command execution

A one-line grep across ~/.claude, ~/.cursor, and .vscode for shell-out patterns in MCP config.

> Part of the **Supply Chain & Incident Response** pack. From the Composed Security blog: [Your MCP server is a shell. Anthropic calls it expected.](https://composedsecurity.com/blog/mcp-stdio-rce).

## Command

```text
grep -rEi "curl|wget|bash -c|sh -c|/tmp/" ~/.claude/ ~/.cursor/ .vscode/ 2>/dev/null
```

## How to use

Copy the command, review every path it touches, then run it in the repository or machine you are investigating. This is a detection command, not a fix.

---

Found this useful? [Composed Security](https://composedsecurity.com) reviews your pull requests for exactly this class of bug.
