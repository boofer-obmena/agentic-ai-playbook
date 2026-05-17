---
id: PATTERN-017
title: "Earned Structure Dynamic Ontology"
title_ru: "Паттерн 17. «Динамическая онтология с заслуженной структурой» (Earned Structure Dynamic Ontology)"
type: pattern
subtype: functional
status: raw
source: "author's development"
date_added: 2026-05-07
version: 1.0
---

# Earned Structure Dynamic Ontology

> **Паттерн 17. «Динамическая онтология с заслуженной структурой» (Earned Structure Dynamic Ontology)**

**Problem:** Rigid, pre-defined ontologies cannot capture new relationships that emerge as the system operates. A mechanism is needed that organically surfaces new relationships without dismantling the verified structure.

**Solution:** The ontology is split into two levels. Hard Core: fixed, repeatedly confirmed relationships. These change only by the Architect's decision. Hypothesis Periphery: dynamic hypothetical relationships, automatically detected by the Auditor. Each hypothesis carries a confirmation counter and, after N independent confirmations, is proposed for promotion to the Hard Core (but promoted only after Architect approval).

**Experimental Verification:** Required. Seed the system with 10 known entity relationships and 3 deliberately ambiguous ones. After 5 audit cycles, verify: the Auditor has surfaced the 3 ambiguous relationships as hypotheses with confirmation counters; none have been auto-promoted without approval.

**Application History:** Not applied. This section is populated based on real-world use of the pattern: task context, what worked, what required adjustment, and final conclusions.
