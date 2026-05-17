---
id: PATTERN-027
title: "Semantic Context Compaction"
title_ru: "Паттерн 27. «Семантически умное сжатие контекста» (Semantic Context Compaction)"
type: pattern
subtype: functional
status: raw
source: "Master All 20 Agentic AI Design Patterns (SOURCE-006); author's development"
date_added: 2026-05-07
version: 1.0
related: []
---

# Semantic Context Compaction

> **Паттерн 27. «Семантически умное сжатие контекста» (Semantic Context Compaction)**

**Problem:** A long-running agent that accumulates tool logs, intermediate results, and multi-page files inevitably reaches the context window limit. The naive solution — deleting the oldest messages — is critically dangerous: the original task or a key constraint set by the user at the very beginning could be lost.

**Solution:** The context is divided into three zones with different processing rules triggered when the fill threshold (~80–90% of the token limit) is reached. Zone 1 — Foundation (start of context): the system prompt and the user's original task. Never compacted; rigidly anchored. Zone 2 — Active Work (end of context): the last N steps of the agent, where the current sub-task is being solved. Preserved in raw form. Zone 3 — Archive (middle portion): intermediate reasoning, logs of failed attempts, contents of already-analyzed and closed files. Compacted into short text summaries.

**Experimental Verification:** Required. Launch an agent on a task designed to fill the context window (processing 50+ files). Verify: the original task and the last N steps are preserved verbatim; after compaction the agent continues working without losing direction; the final result is correct.

**Application History:** Not applied. This section is populated based on real-world use of the pattern: task context, what worked, what required adjustment, and final conclusions.
