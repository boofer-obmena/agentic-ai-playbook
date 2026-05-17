---
id: PATTERN-033
title: "Semantic Query Fan-out"
title_ru: "Паттерн 33. «Семантический веер запросов» (Semantic Query Fan-out)"
type: pattern
subtype: engineering
status: raw
source: "Master All 20 Agentic AI Design Patterns (SOURCE-006); author's development"
date_added: 2026-05-07
version: 1.0
related: ["PATTERN-015", "PATTERN-032"]
---

# Semantic Query Fan-out

> **Паттерн 33. «Семантический веер запросов» (Semantic Query Fan-out)**

**Problem:** A single query to a vector knowledge base can miss the right semantic cluster — especially when the data is unstructured, meaning is expressed indirectly, or a single concept is represented by different words and formulations. The agent issues one query, gets a result that appears relevant, but is in fact just the nearest neighbor in vector space — not what was actually needed. The error goes unnoticed: RAG does not signal that it "found the wrong thing."

**Solution:** Instead of one query, the agent generates N semantically adjacent formulations revolving around a single semantic center — a "fan-out of queries." Each formulation describes the same concept from a different angle: using different words, through related notions, through a contrasting example, through a question about a consequence. All N queries are executed in parallel. The results are aggregated into a "meaning cloud" — a full set of fragments retrieved by the different queries. From this cloud, the agent synthesizes a final answer, explicitly documenting which query retrieved which fragment and what contribution each made to the final conclusion (Chain-of-Thought with traceability). Fragments that appear in the results of multiple queries receive elevated weight — the intersection of multiple formulations indicates high semantic precision.

**Example:** An analyst agent searches a knowledge base for a method to evaluate a counterparty's credit risk. A single query for "credit risk assessment" returns a general article on risk management — not the right result. The agent applies a fan-out: query 1 — "methods for analyzing a counterparty's solvency"; query 2 — "how to determine the probability of default for a counterparty"; query 3 — "scoring models for borrower evaluation"; query 4 — "signs of financial instability in a counterparty." The results of the four queries form a cloud of 12 fragments. Three fragments appeared in the results of two or more queries — they receive elevated weight. The agent synthesizes an answer, citing specific fragments and the queries that found them.

**Related Entities:** Pattern 032 (Agentic RAG with Tool-Augmented Closed Loop) — the patterns complement each other and address different problems. Pattern 032 is about depth: the agent decides whether additional searching is needed, going deeper sequentially. Pattern 033 is about breadth of coverage: the agent initially ensures wide semantic coverage through parallel queries. In complex analytical tasks, both patterns are applied together: first the fan-out provides wide initial coverage, then the iterative loop refines individual directions. Pattern 015 (Operational Metric-Driven Co-Design Loop) — operational metrics are used to evaluate the effectiveness of the query fan-out.

**Precondition:** This pattern is viable only on infrastructure designed according to the throughput capacity principle (see the Key Architectural Principles section). If the latency of a single vector database query is already approaching the acceptable latency threshold, launching a fan-out of N queries will multiply latency by N and make the pattern counterproductive. Before applying the pattern, verify: single-query latency × N queries in the fan-out ≤ the acceptable agent response delay. If the condition is not met — optimize the infrastructure first (chunk size, index type, hot cache) before applying the fan-out.

**Experimental Verification:** Required. Select a knowledge base with unstructured content (literary text, interview transcripts, regulatory documents with vague wording). Formulate 10 questions whose answers exist in the base but are not expressed in obvious terms. Test A: single query. Test B: fan-out of 4 queries with aggregation. Measure: the proportion of questions for which a correct answer was obtained in each mode. Expected improvement in fan-out mode: 30–50% increase in precision on unstructured data.

**Application History:** Not applied. This section is populated based on real-world use of the pattern: task context, what worked, what required adjustment, and final conclusions.
