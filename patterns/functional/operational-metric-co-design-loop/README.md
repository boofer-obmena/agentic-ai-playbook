---
id: PATTERN-015
title: "Operational Metric-Driven Co-Design Loop"
title_ru: "Паттерн 15. «Сквозной цикл улучшения на основе операционных метрик» (Operational Metric-Driven Co-Design Loop)"
type: pattern
subtype: functional
status: raw
source: "author's development"
date_added: 2026-05-07
version: 1.0
---

# Operational Metric-Driven Co-Design Loop

> **Паттерн 15. «Сквозной цикл улучшения на основе операционных метрик» (Operational Metric-Driven Co-Design Loop)**

**Problem:** Standard active learning captures manual corrections to artifact content, but misses inefficiency in the agent's own approach: choosing an unnecessarily long route, using a GUI where an API exists.

**Solution:** A "Task Efficiency Score" metric is introduced. Any manual human intervention — representing a deviation from the agent's plan — automatically creates a training pair: "Suboptimal agent plan → Preferred human plan." After accumulating several examples, the agent begins to independently choose more efficient routes.

**Experimental Verification:** Required. Create a task that can be solved via two routes: a short API-based path and a long GUI-based path. After 3 manual corrections steering the agent toward the API path, verify that the agent chooses the API path autonomously on the 4th attempt.

**Application History:** Not applied. This section is populated based on real-world use of the pattern: task context, what worked, what required adjustment, and final conclusions.
