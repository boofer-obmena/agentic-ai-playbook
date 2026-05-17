---
id: PATTERN-025
title: "Three-Layer Agent Rules Architecture"
title_ru: "Паттерн 25. «Трёхуровневая архитектура правил агента» (Three-Layer Agent Rules Architecture)"
type: pattern
subtype: functional
status: applied
source: "Master All 20 Agentic AI Design Patterns (SOURCE-006); author's development; applied on Mac Mini (April 2026)"
date_added: 2026-05-07
version: 1.0
related: ["PATTERN-010", "PATTERN-020"]
---

# Three-Layer Agent Rules Architecture

> **Паттерн 25. «Трёхуровневая архитектура правил агента» (Three-Layer Agent Rules Architecture)**

**Problem:** An agent's system prompt is a static artifact: only a developer can change it, and only manually. If everything is placed there — role, security rules, current infrastructure configuration, IP addresses, paths — the prompt becomes bloated and stale. The agent operates with outdated data until the next manual update.

**Solution:** Agent rules are separated into three independent layers with different access rights and different rates of change. Layer 1 — Foundation (system prompt): agent role, categorical prohibitions, response format, an instruction to "read the rules file on startup." Changed only by the system owner, manually. Layer 2 — Operational Rules (server_rules.md file): current infrastructure configuration, IP addresses, paths, validated behavioral rules. The agent reads the file on every startup via read_file. Layer 3 — Notes (server_notes.md file): observations, rule candidates, improvement hypotheses. Populated by the reviewer agent autonomously. After verification, items are promoted to Layer 2.

Separation principle: Into the system prompt — only what NEVER changes. Into the rules file — everything operational. Into notes — candidates that have not passed verification.

**Related Entities:** Pattern 20 (Ratchet Loop) — Layer 3 (Notes) serves as the input to the self-improvement loop. Pattern 10 (Agent Tool Manifest) — Layer 2 may contain the current agent tool manifest.

**Experimental Verification:** Required. Change an IP address in the rules file (Layer 2) without modifying the system prompt. Verify: the agent uses the new IP on the next session without a restart. The system prompt remains untouched.

**Application History:** Applied during the creation of a Mac Mini server-admin agent (April 2026). The three-layer structure was developed empirically through operational experience. Key insight: separating the foundation from operational data allowed infrastructure configuration to be updated without manual editing of the system prompt.
