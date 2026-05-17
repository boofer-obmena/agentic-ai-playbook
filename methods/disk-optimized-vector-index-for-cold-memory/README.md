---
id: METHOD-006
title: "Disk-Optimized Vector Index for Cold Memory"
title_ru: "Экономичный дисковый индекс для долгой памяти (Disk-Optimized Vector Index for Cold Memory)"
type: method
status: raw
subtype: "method / technique"
source: "author's development"
date_added: 2026-05-07
version: 1.0-preview
---

# Disk-Optimized Vector Index for Cold Memory

> **Экономичный дисковый индекс для долгой памяти (Disk-Optimized Vector Index for Cold Memory)**

**Problem:** An agent system's long-term memory (logs, old artifact versions, incident history) can far exceed available RAM. Storing everything in RAM is economically and technically impractical. At the same time, shifting all search to slow storage is unacceptable due to response time degradation.

**Solution:** Data is split into two storage tiers based on access frequency. Hot index (RAM): frequently accessed data — the last N days, active tasks, frequently queried documents. Stored in memory, delivers minimal search latency. Cold index (SSD): historical data, archived versions, rarely queried documents. Uses the DiskANN algorithm, which builds a search graph directly on disk, providing acceptable search latency without loading data into RAM. The Financial Controller manages the balance between the two tiers, automatically moving data between the hot and cold indices based on access frequency.

**Example:** The Auditor analyzes a three-month-old incident. The incident data resides in the cold index. The search query is routed to the SSD index. Search latency is higher than for the hot index, but remains within the acceptable threshold. RAM is not consumed by rarely accessed data.

**Experimental Verification:** Populate the system with data whose volume is twice the available RAM. Run a mixed query stream: 70% to recent data, 30% to archival data. Verify: the system is stable, does not exhaust RAM; response time for hot data is within the strict SLA; response time for cold data is within the extended SLA.

**Application History:** Not applied. This section is populated based on real-world use of the method: task context, what worked, what required adjustment, and final conclusions.

**When to Use:** [Requires author refinement — to be finalized in Phase 4]

**Limitations:** [Requires author refinement — to be finalized in Phase 4]

Related Patterns: [Requires author refinement — to be populated in Phase 4]
