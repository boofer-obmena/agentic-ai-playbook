---
id: PATTERN-034
title: "Agent First-Token Response"
title_ru: "Паттерн 34. «Первый отклик агента» (Agent First-Token Response)"
type: pattern
subtype: engineering
status: raw
source: "Master All 20 Agentic AI Design Patterns (SOURCE-006); author's development"
date_added: 2026-05-07
version: 1.0
related: []
---

# Agent First-Token Response

> **Паттерн 34. «Первый отклик агента» (Agent First-Token Response)**

**Problem:** An agent, upon receiving a complex request, begins processing and goes silent — sometimes for tens of seconds. The user or calling agent has no way to tell whether the system is still working or has frozen. This undermines perceived interaction quality. Research shows that a delay exceeding 2–3 seconds before the first signal is perceived as a failure, even if the final answer is excellent. The problem is especially critical for analytical agents with long processing times — KB Manager, Requirements Analyst, Agent-Auditor.

**Solution:** The agent must immediately — before beginning the main processing — deliver a short acknowledgment of task receipt. This is the "first token": a minimal signal communicating that the task has been accepted and processing has begun. The acknowledgment includes: confirmation of request receipt, a brief description of what the agent intends to do, and, if necessary, a time estimate. After that, the agent proceeds to main processing and returns the result. For long-running tasks, streaming intermediate results as they become ready is recommended — instead of delivering the entire response at once. This transforms waiting from anxious to informed.

**Example:** An analyst agent receives a task: "Analyze all open tasks for the quarter and identify systemic bottlenecks." Standard behavior: 40 seconds of silence, then a full report. Pattern-compliant behavior: immediate response — "Received. Analyzing 47 open tasks for Q1 2025. Starting with grouping by assigned agent." Then after 15 seconds: "First result: 12 tasks are stuck at the QA validation stage. Continuing analysis..." Then the final report. The user is continuously aware that the system is working and making progress.

**Experimental Verification:** Required. Conduct user testing with two groups. Group A receives agent responses without a first token (silence → result). Group B receives an immediate acknowledgment + intermediate updates → result. The actual processing time is identical in both groups. Measure: subjective rating of system quality, proportion of users who interrupted the wait. Expected result: perceived quality in Group B is significantly higher at identical actual quality.

**Application History:** Not applied. This section is populated based on real-world use of the pattern: task context, what worked, what required adjustment, and final conclusions.
