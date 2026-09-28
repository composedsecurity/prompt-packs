---
title: "Grep for the postinstall campaign IOCs"
slug: "sweep-postinstall-iocs"
category: "supply-chain"
type: "command"
tags: ["supply-chain", "ioc", "detection"]
source: "https://composedsecurity.com/blog/postinstall-hook-700-repos"
source_label: "IoC sweep"
---

# Grep for the postinstall campaign IOCs

Search manifests, lockfiles, and CI YAML for the campaign's indicators of compromise.

> Part of the **Supply Chain & Incident Response** pack. From the Composed Security blog: [700 repos. One postinstall hook.](https://composedsecurity.com/blog/postinstall-hook-700-repos).

## Command

```text
grep -rE "parikhpreyash4|/tmp/\.sshd|gvfsd-network|curl -skL" \
  package.json package-lock.json .github/ \
  --include="*.json" --include="*.yml" --include="*.yaml"
```

## How to use

Copy the command, review every path it touches, then run it in the repository or machine you are investigating. This is a detection command, not a fix.

---

Found this useful? [Composed Security](https://composedsecurity.com) reviews your pull requests for exactly this class of bug.
