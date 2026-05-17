---
id: PATTERN-013
title: "Compensating Saga for AI-Powered Operations"
title_ru: "Паттерн 13. «Компенсационная сага» (Compensating Saga for AI-Powered Operations)"
type: pattern
subtype: functional
status: raw
source: "author's development"
date_added: 2026-05-07
version: 1.0
---

# Compensating Saga for AI-Powered Operations

> **Паттерн 13. «Компенсационная сага» (Compensating Saga for AI-Powered Operations)**

**Problem:** Many operations in agent systems involve calls to external systems that cannot be rolled back in a standard way. If a failure occurs mid-way through a multi-step operation, the system is left in a partially executed state.

**Solution:** Every high-level operation that spans multiple external systems is designed as a Saga. Each step has an explicitly defined compensating action — an operation that semantically "undoes" the effect of the primary step. On failure, the Orchestrator invokes compensating actions in reverse order until a consistent initial state is reached.

**Example:** The Developer Agent creates a Pull Request (step 1). It then attempts to create a linked task in the tracker (step 2) — the tracker is unavailable. The Orchestrator invokes the compensating action for step 1: closes the Pull Request with the comment "Automatically closed: pipeline failure at step 2."

**Experimental Verification:** Required. Model a saga of 3 steps where step 2 fails. Verify that compensation is invoked for step 1 only, and the system reaches a consistent state.

**Application History:** Not applied. This section is populated based on real-world use of the pattern: task context, what worked, what required adjustment, and final conclusions.
