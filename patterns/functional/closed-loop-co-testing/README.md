---
id: PATTERN-024
title: "Closed-Loop Co-Testing"
title_ru: "Паттерн 24. «Замкнутый цикл совместного тестирования» (Closed-Loop Co-Testing)"
type: pattern
subtype: functional
status: raw
source: "Master All 20 Agentic AI Design Patterns (SOURCE-006); author's development"
date_added: 2026-05-07
version: 1.0
related: ["PATTERN-020", "PATTERN-033"]
---

# Closed-Loop Co-Testing

> **Паттерн 24. «Замкнутый цикл совместного тестирования» (Closed-Loop Co-Testing)**

**Problem:** Testing of a communication agent and a knowledge base is conducted in isolation and sequentially. This doubles the time and resource cost, and — more importantly — yields no information about the quality of interaction between the components under real conditions. The communication agent and the knowledge base can individually show acceptable results, yet produce poor quality in combination.

**Solution:** The two components are tested jointly in a closed iterative loop. The communication agent generates fan-out queries (per Pattern E9) and directs them to the knowledge base. The KB returns a cloud of chunks. The Field Analyst — a subject-matter expert on the knowledge base domain — evaluates the relevance of the KB's responses. The Tester agent manages the loop and evaluates the quality of the communication agent's queries. A single run of the loop yields two independent quality measurements: a metric for the communication agent and a metric for the knowledge base. The loop iterates — not linear, but closed.

Participants: Communication Agent (generates queries) → Knowledge Base (returns chunks) → Field Analyst (evaluates KB response quality) → Tester (manages the loop, evaluates communication agent query quality).

Principle behind the pattern: Look for architectural situations where testing multiple components can be combined into a closed loop — a single process evaluates several participants at once. Not a linear run, but a loop. Applicable to two, three, or more components simultaneously.

**Related Entities:** Pattern 033 (Semantic Query Fan-out) — the communication agent applies the fan-out query technique. Pattern 20 (Ratchet Loop) — test results become the foundation for improving both communication agent prompts and knowledge base content.

**Experimental Verification:** Required. Deploy a test scenario: a KB with known content, a communication agent, an analyst, and a tester. Run 5 loop iterations. Measure: the trajectory of the communication agent's query accuracy metric (should rise), the trajectory of KB chunk relevance (reveals indexing weak spots). Compare with isolated testing of the same components: total time and completeness of issues discovered.

**Application History:** Not applied. This section is populated based on real-world use of the pattern: task context, what worked, what required adjustment, and final conclusions.
