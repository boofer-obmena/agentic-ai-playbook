---
id: PATTERN-020
title: "Ratchet Loop"
title_ru: "Паттерн 20. «Ratchet Loop / Храповой цикл самоулучшения» (Ratchet Loop)"
type: pattern
subtype: functional
status: applied
source: "author's development; applied on Mac Mini (April 2026)"
date_added: 2026-05-07
version: 1.0
related: ["PATTERN-002", "PATTERN-025"]
---

# Ratchet Loop

> **Паттерн 20. «Ratchet Loop / Храповой цикл самоулучшения» (Ratchet Loop)**

**Problem:** Agent systems degrade without a self-improvement mechanism. Accumulated operational experience — errors, observations, edge cases — is not converted into improvements in the agent's behavioral rules. The system remains static despite a growing body of information about its own weaknesses.

**Solution:** A closed loop is introduced: Observe → Hypothesize → Test → Commit Improvement. A reviewer-agent analyzes the agent's interaction history over a period on a schedule, formulates hypotheses about rule improvements, and writes them to an intermediate buffer (e.g., `server_notes.md`). After verification, confirmed hypotheses are migrated to the main rule set (`server_rules.md`). The "ratchet" principle: the system only moves forward — confirmed improvements are never rolled back, unconfirmed hypotheses never enter the rules automatically.

**Example:** A server-admin agent attempted to run a command without `sudo` three times in a week and received an error each time. The reviewer-agent detects the pattern and formulates a hypothesis: "Add rule: before commands requiring elevated privileges, check for `sudo`." The hypothesis is placed in the buffer. The Architect verifies it and migrates the rule to the main set. The agent's next iteration already operates with the updated rules.

**Related Entities:** Pattern 25 (Three-Level Rule Architecture) — the hypothesis buffer is Level 3 of the three-level architecture. Pattern 2 (Active Traceability) — the reviewer-agent is a specialized implementation of the Auditor.

**Experimental Verification:** Deliberately introduce a systematic error into the agent's behavior (e.g., incorrect tool invocation order). Run the reviewer-agent. Verify: the reviewer detects the error pattern, formulates a concrete improvement hypothesis, and writes it to the buffer. After manual confirmation, the rule is added to the main set. The next agent run does not reproduce the error.

### Autonomy Progression

**Level 1** — The agent executes explicitly assigned tasks; does not modify its own behavior.

**Level 2** — The agent captures observations and proposes improvements for human review.

**Level 3** — The agent autonomously applies improvements within pre-approved boundaries, logging changes.

**Level 4 (limit)** — The agent creates tasks for other agents, which execute them, test them, and report results to yet other agents. The human performs only the final approval function (an "approve" button). Level 4 benchmark: ~90% of tasks executed autonomously. Most production systems today operate at levels 2–3. Level 4 is a 2–3 year design horizon.

**Application History:** Partially implemented during the creation of the Mac Mini server-admin agent (April 2026). The reviewer-agent runs on a schedule at 05:00, reads `agent_chat_memory` for the preceding 24 hours, and formulates observations in `server_notes.md`. Corresponds to autonomy progression levels 2–3. What required adjustment: the boundary between "observation" and "rule" proved fuzzy — criteria for transitioning a hypothesis from the buffer into the rules need to be formalized.
