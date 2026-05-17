---
id: PATTERN-038
title: "Gradient Data Storage"
title_ru: "Паттерн 38. «Градиентное хранение данных» (Gradient Data Storage)"
type: pattern
subtype: engineering
status: raw
source: "Master All 20 Agentic AI Design Patterns (SOURCE-006); author's development"
date_added: 2026-05-07
version: 1.0
related: []
---

# Gradient Data Storage

> **Паттерн 38. «Градиентное хранение данных» (Gradient Data Storage)**

**Problem:** Not all data has the same access frequency or retrieval speed requirements. Storing everything in fast RAM is too expensive. Storing everything in slow long-term storage is too slow for active tasks.

**Solution:** Data is distributed across three storage tiers based on access frequency and latency sensitivity. Hot tier (RAM / cache): active context of the current task, frequently requested rules, the agent's "desktop." Warm tier (SSD / local DB): vector indices, history of the last N sessions, the project's active knowledge base. Cold tier (HDD / archival storage): historical logs, archived artifact versions, data from completed projects. Data automatically migrates between tiers according to defined rules (for example, data not accessed for 30 days moves from warm to cold tier).

**Example:** To be developed.

**Related Entities:** To be developed.

**Precondition:** To be developed.

**Experimental Verification:** To be developed.

**Application History:** Not applied. This section is populated based on real-world use of the pattern: task context, what worked, what required adjustment, and final conclusions.
