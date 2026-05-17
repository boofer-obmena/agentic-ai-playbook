---
id: PATTERN-037
title: "Multi-Vector Semantic Index"
title_ru: "Паттерн 37. «Мультивекторный семантический индекс» (Multi-Vector Semantic Index)"
type: pattern
subtype: engineering
status: raw
source: "Master All 20 Agentic AI Design Patterns (SOURCE-006); author's development"
date_added: 2026-05-07
version: 1.0
related: []
---

# Multi-Vector Semantic Index

> **Паттерн 37. «Мультивекторный семантический индекс» (Multi-Vector Semantic Index)**

**Problem:** A single way of representing a document in vector space does not capture all aspects of its content. A query about a technical error does not find a document that describes the same problem in business process terms. A search for an exact formulation misses semantically close but differently worded fragments.

**Solution:** Each document is indexed in several ways simultaneously: Full-text vector representation (dense embedding): semantic proximity. Keywords (BM25 / sparse): exact term matches. Document summary: high-level meaning. Structured metadata: document type, date, author, related systems. At query time, hybrid search is used: results from different indices are weighted and combined through a ranking algorithm (Reciprocal Rank Fusion or equivalent).

**Example:** To be developed.

**Related Entities:** To be developed.

**Precondition:** To be developed.

**Experimental Verification:** Required. Prepare a set of 20 test queries with known relevant documents. Compare recall@10 for single-vector and multi-vector indices. Expected result: the multi-vector index shows 20–40% higher recall.

**Application History:** Not applied. This section is populated based on real-world use of the pattern: task context, what worked, what required adjustment, and final conclusions.
