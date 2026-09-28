---
title: "Audit cloud infrastructure for breach modes"
slug: "audit-cloud-infrastructure"
category: "supply-chain"
type: "prompt"
tags: ["cloud", "aws", "audit"]
source: "https://composedsecurity.com/blog/fulcrumsec-global-schools-breach"
source_label: "Hand to your agent"
---

# Audit cloud infrastructure for breach modes

S3 public-access blocks, SCP enforcement, secret rotation, credential reuse, and IR playbook coverage.

> Part of the **Supply Chain & Incident Response** pack. From the Composed Security blog: [12,000 Passwords. All the Same One.](https://composedsecurity.com/blog/fulcrumsec-global-schools-breach).

## Prompt

```text
Audit our cloud infrastructure for the Global Schools failure modes.

1. Check S3 bucket public access settings.
   Run `aws s3api list-buckets` then for each:
   `aws s3api get-public-access-block --bucket <name>`.
   Flag any bucket without BlockPublicAcls, BlockPublicPolicy,
   IgnorePublicAcls, or RestrictPublicBuckets set to true.

2. Check AWS Organizations SCP for s3:BlockPublicAccess.
   If no SCP enforces it, propose one.

3. Inventory our secrets manager entries. List every secret,
   when it was last rotated, and which services use it.
   Flag any secret not rotated in the last 90 days.

4. Check credential uniqueness across user database.
   Run a hash comparison on password fields (without reading values).
   Flag any reuse rate above 0%.

5. Review incident response playbook. Confirm it includes
   a mandatory credential rotation step as part of the
   recovery checklist, not as an optional post-mortem action.
```

## How to use

Paste the block above into your coding agent (Cursor, Claude Code, Codex, Lovable, or Bolt). Give it read access to the repo. Keep it read-only where the prompt says so, and verify each finding before acting on it.

---

Found this useful? [Composed Security](https://composedsecurity.com) reviews your pull requests for exactly this class of bug.
