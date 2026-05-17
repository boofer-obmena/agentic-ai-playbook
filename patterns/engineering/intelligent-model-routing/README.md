---
id: PATTERN-036
title: "Intelligent Model Routing"
title_ru: "Паттерн 36. «Интеллектуальная маршрутизация с самооценкой сложности» (Intelligent Model Routing)"
type: pattern
subtype: engineering
status: raw
source: "Master All 20 Agentic AI Design Patterns (SOURCE-006); author's development"
date_added: 2026-05-07
version: 1.0
related: []
---

# Intelligent Model Routing

> **Паттерн 36. «Интеллектуальная маршрутизация с самооценкой сложности» (Intelligent Model Routing)**

**Problem:** All requests are processed by the same powerful LLM regardless of task complexity. Updating a task status in a tracker, routing an incoming message by category, checking a field format — none of these operations require a powerful model. Using excessive resources leads to unnecessary computational overhead.

**Solution:** Each request undergoes a preliminary complexity assessment. The agent explicitly sets a complexity flag based on the task's characteristics. The router directs the request to the appropriate resource according to a "Task Type → Model" map. Simple tasks: deterministic operations (format validation, status updates, keyword-based routing) — routed to a raw SQL query or RegEx handler without an LLM. Standard tasks: data structuring, entity extraction, generating standard artifacts — a lightweight or medium LLM. Complex tasks: analytics, architectural decisions, ambiguity resolution — a full-power LLM with thinking mode.

**Example:** A pipeline receives 100 requests per hour. 45 — status updates for tasks (Simple, direct SQL). 30 — generating standard functional requirements (FR) from a template (Standard, medium LLM). 25 — analytics of complex requirements with contradictions (Complex, full-power LLM). As a result of routing: 45% of requests consume no LLM resources at all, 30% — minimal resources, only 25% — maximum resources.

**Experimental Verification:** Required. Prepare a mixed set of 100 tasks with a known optimal model for each (Simple/Standard/Complex). Run through the router. Measure: classification accuracy (proportion of tasks directed to the optimal resource) and total GPU budget expenditure. Goal: 40%+ cost reduction while maintaining result quality.

**Application History:** Not applied. This section is populated based on real-world use of the pattern: task context, what worked, what required adjustment, and final conclusions.
