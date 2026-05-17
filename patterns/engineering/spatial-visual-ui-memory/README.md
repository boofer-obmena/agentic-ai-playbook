---
id: PATTERN-040
title: "Spatial-Visual UI Memory"
title_ru: "Паттерн 40. «Пространственно-визуальная память интерфейсов» (Spatial-Visual UI Memory)"
type: pattern
subtype: engineering
status: raw
source: "Master All 20 Agentic AI Design Patterns (SOURCE-006); author's development"
date_added: 2026-05-07
version: 1.0
related: ["PATTERN-011"]
---

# Spatial-Visual UI Memory

> **Паттерн 40. «Пространственно-визуальная память интерфейсов» (Spatial-Visual UI Memory)**

**Problem:** A significant portion of enterprise software exposes no API and is managed exclusively through a graphical interface. An agent working with such software, when an unforeseen situation arises (a pop-up window, a change in interface state), does not know what the previous context was and cannot correctly continue executing the task.

**Solution:** At each step of GUI interaction, a "visual state snapshot" is saved — a compact representation of the interface's accessibility tree with element coordinates, their types, and textual content. The snapshot is saved as part of a checkpoint (Pattern 011). When a divergence arises between the current interface state and the last saved snapshot, the agent detects the change, identifies new elements (e.g., a modal window), and decides how to handle the change before continuing the main task.

**Example:** A first-line support agent executes a sequence of actions in an ERP system. At step 3, a system notification pops up with an "Accept" button. The agent compares the current accessibility tree with the saved snapshot from step 2. It detects a new element (a modal window), identifies it as a system notification and closes it. It returns to the main task, continuing from step 3.

**Related Entities:** Pattern 011 (Orchestrator-Driven Explicit State Flow) — the orchestrator's checkpoints serve as the mechanism for saving visual state snapshots.

**Experimental Verification:** Required. Create a test scenario of 5 steps of interacting with an application. At step 2, trigger a modal window programmatically. Verify: the agent detects the divergence from the saved tree of step 1, correctly identifies and handles the new element, resumes execution at the correct step.

**Application History:** Not applied. This section is populated based on real-world use of the pattern: task context, what worked, what required adjustment, and final conclusions.
