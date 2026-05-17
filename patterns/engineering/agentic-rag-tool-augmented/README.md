---
id: PATTERN-032
title: "Agentic RAG with Tool-Augmented Closed Loop"
title_ru: "Паттерн 032. «Агентный поиск с инструментальным замкнутым циклом» (Agentic RAG with Tool-Augmented Closed Loop)"
type: pattern
subtype: engineering
status: raw
source: "Master All 20 Agentic AI Design Patterns (SOURCE-006); author's development"
date_added: 2026-05-07
version: 1.0
related: []
---

# Agentic RAG with Tool-Augmented Closed Loop

> **Паттерн 032. «Агентный поиск с инструментальным замкнутым циклом» (Agentic RAG with Tool-Augmented Closed Loop)**

**Problem:** Standard RAG (single search → answer) is insufficient for analytical tasks that require iterative investigation: first find the big picture, then refine details, then perform a calculation. An agent limited to a single search query either gives a superficial answer or hallucinates the missing details.

**Solution:** The agent receives an extended Agent Tool Manifest that includes not only search tools but also analytical tools: search_in_knowledge_base (knowledge base search), calculator (arithmetic calculations), date_calculator (date and period operations), cross_reference (cross-checking between two sources). The agent independently decides how many "search → analyze → re-search" iterations it needs to form a well-grounded answer. Every tool invocation is recorded in the Chain-of-Thought and is available for audit.

**Example:** Task: "Sum the planned effort for all open tasks assigned to developer Ivanov in Q1 2025 and compare with actual hours from the time-tracking system." The agent: (1) invokes search_in_knowledge_base with a query about Ivanov's tasks in Q1 2025, receives a list of 7 tasks; (2) for each task, invokes search_in_knowledge_base to obtain the planned hour budget; (3) invokes calculator to sum the planned hours; (4) invokes search_in_knowledge_base to obtain actual hours from the time-tracking system; (5) invokes calculator to compute the deviation; (6) produces an answer citing each step and data source.

**Experimental Verification:** Required. Formulate a task that demonstrably requires at least 3 search iterations and at least 1 calculation. Verify: the agent performs the necessary number of tool invocations, each invocation is documented in the Chain-of-Thought, the final answer is accurate and cites the source of each number.

**Application History:** Not applied. This section is populated based on real-world use of the pattern: task context, what worked, what required adjustment, and final conclusions.
