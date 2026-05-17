---
id: PATTERN-031
title: "Seamless Model Rotation in Vector Store"
title_ru: "Паттерн 031. «Непрерывная ротация моделей без остановки конвейера» (Seamless Model Rotation in Vector Store)"
type: pattern
subtype: engineering
status: raw
source: "Master All 20 Agentic AI Design Patterns (SOURCE-006); author's development"
date_added: 2026-05-07
version: 1.0
related: []
---

# Seamless Model Rotation in Vector Store

> **Паттерн 031. «Непрерывная ротация моделей без остановки конвейера» (Seamless Model Rotation in Vector Store)**

**Problem:** Updating the model used to generate vector embeddings requires a full reindexing of the entire knowledge base. With a significant data volume, this process takes days and requires stopping the pipeline: it is impossible to simultaneously serve queries with old embeddings and generate new ones.

**Solution:** A multi-vector indexing mechanism is used. When updating the model, the new model is registered in the vector database in parallel with the old one. The indexes coexist. A search query is executed against both indexes simultaneously; results are ranked and merged. A background process recalculates embeddings for all documents using the new model. As fragments become ready, searches against them switch to the new index. After the full recalculation completes, the old index is removed. The pipeline is never interrupted at any stage.

**Example:** A knowledge base contains 50,000 documents. Recalculating embeddings with the new model takes 8 hours. During those 8 hours, the pipeline continues serving queries. For each query: documents already reindexed by the new model are searched via the new index; those not yet reindexed — via the old one. Search quality does not degrade; response time remains within SLA.

**Experimental Verification:** Required. Launch an active stream of search queries while tracking latency and relevance. Simultaneously, launch a background reindexing of 50% of the base. Verify during reindexing: response latency has not exceeded SLA, relevance of results has not declined.

**Application History:** Not applied. This section is populated based on real-world use of the pattern: task context, what worked, what required adjustment, and final conclusions.
