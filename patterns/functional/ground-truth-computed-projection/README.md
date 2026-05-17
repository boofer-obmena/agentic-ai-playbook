---
id: PATTERN-008
title: "Ground Truth vs. Computed Projection"
title_ru: "Паттерн 8. «Фундаментальный источник против вычисляемой проекции» (Ground Truth vs. Computed Projection)"
type: pattern
subtype: functional
status: raw
source: "author's development"
date_added: 2026-05-07
version: 1.0
---

# Ground Truth vs. Computed Projection

> **Паттерн 8. «Фундаментальный источник против вычисляемой проекции» (Ground Truth vs. Computed Projection)**

**Problem:** When an agent synthesizes a final artifact (technical specification, report, analytical note), it tends to "polish" the input data: smooth over contradictions, pick one of several competing facts, and construct a clean narrative. This destroys signals about real discrepancies. A cascade of distortions accumulates.

**Solution:** The data system is strictly separated into two independent layers. The Ground Truth Layer: immutable, versioned records in a database. Facts are never overwritten — only new versions are appended. Each fact contains metadata: source, recording date, signal accuracy coefficient. The Computed Projection Layer: technical specifications, code, analytical reports, and any synthesized artifacts. Projections are created for a specific query and are temporary. Data corrections are always made in the fact layer, after which the system automatically rebuilds all dependent projections.

**Example:** A functional architect discovers an error in the technical specification: a data type for a field is specified incorrectly. In the target architecture: the architect corrects the record in the FR Registry (fact layer). The system automatically rebuilds the technical specification, generates updated test cases, and notifies the developer of the change.

**Experimental Verification:** Enter two mutually contradictory requirements into the fact layer. In the target mode, the agent must explicitly highlight a "Critical Contradiction" block indicating both competing facts and request resolution from a human.

**Application History:** Not applied. This section is populated based on real-world use of the pattern: task context, what worked, what required adjustment, and final conclusions.
