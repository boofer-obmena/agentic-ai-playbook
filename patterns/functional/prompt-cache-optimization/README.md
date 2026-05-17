---
id: PATTERN-028
title: "Prompt Cache Optimization"
title_ru: "Паттерн 28. «Статика вперёд, динамика в конец» (Prompt Cache Optimization)"
type: pattern
subtype: functional
status: raw
source: "Master All 20 Agentic AI Design Patterns (SOURCE-006); author's development"
date_added: 2026-05-07
version: 1.0
related: []
---

# Prompt Cache Optimization

> **Паттерн 28. «Статика вперёд, динамика в конец» (Prompt Cache Optimization)**

**Problem:** Every language model call is billed by the number of input tokens. An agent in a loop makes dozens of iterations, each time sending the system prompt. If the prompt begins with dynamically changing content (current time, a variable's status), the cache is invalidated on every iteration. On long tasks, this turns the agent into a financial black hole.

**Solution:** The system prompt is assembled according to a strict principle: static content — always first, dynamic content — always at the end. Static content: agent role, categorical rules, tool descriptions, configuration file contents — everything that does not change between iterations. Dynamic content: current working directory, system time, current task status, last tool call result. Providers use prefix caching: if the beginning of the prompt matches the previous call, those tokens are served from the cache without recomputation.

**Experimental Verification:** Required. Configure cache_hit / cache_miss logging on the provider side. Run the agent in two configurations: static-first and dynamic-first. Measure the cache_hit proportion and the actual cost of a run. Expected result: the correct configuration yields 70–90% cache_hit on static tokens.

**Application History:** Not applied. This section is populated based on real-world use of the pattern: task context, what worked, what required adjustment, and final conclusions.
