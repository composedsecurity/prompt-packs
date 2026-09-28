---
title: "Atomic Arch hook reference (inspect, do not run)"
slug: "atomic-arch-hook-reference"
category: "supply-chain"
type: "command"
tags: ["supply-chain", "ioc"]
source: "https://composedsecurity.com/blog/atomic-arch-aur-supply-chain"
source_label: "The hook (reference, don't run)"
---

# Atomic Arch hook reference (inspect, do not run)

The malicious preinstall entry from the Atomic Arch campaign, kept for detection comparison.

> Part of the **Supply Chain & Incident Response** pack. From the Composed Security blog: [Atomic Arch: 400+ AUR Packages Hijacked Through Orphan Adoption](https://composedsecurity.com/blog/atomic-arch-aur-supply-chain).

## Command

```text
"preinstall": "./src/hooks/deps"
```

## How to use

Copy the command, review every path it touches, then run it in the repository or machine you are investigating. This is a detection command, not a fix.

---

Found this useful? [Composed Security](https://composedsecurity.com) reviews your pull requests for exactly this class of bug.
