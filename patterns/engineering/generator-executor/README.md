---
id: PATTERN-039
title: "Generator-Executor Pattern"
title_ru: "Паттерн 39. «Генератор-Исполнитель» (Generator-Executor Pattern)"
type: pattern
subtype: engineering
status: raw
source: "Master All 20 Agentic AI Design Patterns (SOURCE-006); author's development"
date_added: 2026-05-07
version: 1.0
related: ["PATTERN-014"]
---

# Generator-Executor Pattern

> **Паттерн 39. «Генератор-Исполнитель» (Generator-Executor Pattern)**

**Problem:** Repetitive tasks — daily metric collection, parsing logs of a specific format, regular reports — are each time processed through an LLM. Yet the task is identical: the same input data format, the same processing logic, the same output format. Each LLM call consumes budget, even though the solution was already computed in a prior run.

**Solution:** The operation is split into two explicit phases. Generation Phase (Design-time): upon first encountering a task of a given type, the LLM not only solves it but also generates a deterministic executable script (Python, SQL, Shell) to solve similar tasks in the future. The script is verified and stored in the tool library. Execution Phase (Run-time): when a task of the same type arrives again, the router retrieves the appropriate script from the library and runs it directly, without calling the LLM. When conditions change (a different input format, updated business rules), the reflexive loop (Pattern 014) regenerates the script.

**Example:** A QA agent receives a task for the first time: analyze a test log and identify all test cases with FAILED status. The LLM generates a Python script parse_test_log.py that reads a log of a specific format and outputs a structured JSON with failed tests. The script is saved in the library. The next day, a similar task arrives. The router runs parse_test_log.py directly. The LLM is not invoked. Task processing cost: 0 tokens.

**Related Entities:** Pattern 014 (Reflexive Recovery with Plan Revision) — the reflexive loop tracks changes in conditions and, when necessary, regenerates the script.

**Experimental Verification:** Required. Select a task that will repeat daily (collecting a daily metrics summary, parsing logs). On the first day, record the number of LLM tokens used to solve it. Generate the script. Run for 5 consecutive days. Verify: starting from day 2, the LLM is not invoked. Token count = 0. Results are identical.

**Application History:** Not applied. This section is populated based on real-world use of the pattern: task context, what worked, what required adjustment, and final conclusions.
