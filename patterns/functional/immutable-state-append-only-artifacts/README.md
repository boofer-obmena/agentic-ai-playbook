---
id: PATTERN-009
title: "Immutable State & Append-Only Artifacts"
title_ru: "Паттерн 9. «Неизменяемые состояния и версионирование артефактов» (Immutable State & Append-Only Artifacts)"
type: pattern
subtype: functional
status: raw
source: "author's development"
date_added: 2026-05-07
version: 1.0
---

# Immutable State & Append-Only Artifacts

> **Паттерн 9. «Неизменяемые состояния и версионирование артефактов» (Immutable State & Append-Only Artifacts)**

**Problem:** Shared Mutable State is the most dangerous anti-pattern in multi-agent systems. When several agents have access to the same mutable object, state races arise: agent B overwrites agent A's result. Data loss occurs silently, without any errors or warnings.

**Solution:** All critical data and artifacts are made immutable. Any change is not an overwrite of an existing record but the creation of a new version with a new identifier. Data is append-only. At each agent invocation, the Orchestrator explicitly passes it a specific, pinned version of the data. If two agents concurrently produce competing versions of the same artifact, the Orchestrator initiates a conflict resolution transaction with human involvement.

**Example:** Two developer agents work on the same module in parallel and both create version 2.2. In a system with mutable state, one of the results is silently overwritten. In the target architecture, the Orchestrator detects the conflict and initiates a "Version Conflict Resolution" task with both versions up for review.

**Experimental Verification:** Deliberately launch two agents to work on the same module simultaneously. Record the result: both versions are preserved independently, none is lost, and a conflict resolution task is created.

**Application History:** Not applied. This section is populated based on real-world use of the pattern: task context, what worked, what required adjustment, and final conclusions.

### Warning: Agent Memory as a Critical Asset

An agent that works on a team over a long period and accumulates collective context (decisions, communication nuances, past failures and successes) gradually becomes the primary carrier of corporate or project memory. Losing this memory is equivalent to the sudden departure of the team's most experienced member.

Requirement for the architect: agent memory is a critical asset and requires scheduled backups, versioning (the ability to roll back to a previous state), and documentation (understanding what exactly is stored and in what format).
