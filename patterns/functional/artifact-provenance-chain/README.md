---
id: PATTERN-001
title: "Artifact Provenance Chain"
title_ru: "Паттерн 1. «Цепочка происхождения артефакта» (Artifact Provenance Chain)"
type: pattern
subtype: functional
status: raw
source: "author's development"
date_added: 2026-05-07
version: 1.0
---

# Artifact Provenance Chain

> **Паттерн 1. «Цепочка происхождения артефакта» (Artifact Provenance Chain)**

**Problem:** During multi-step artifact transformations, the lineage is lost: it becomes unclear what the current result was derived from and why. When a technical specification is created from functional requirements, functional requirements from a User Story, and the User Story from an interview, the provenance chain breaks easily. Any participant in the process must be able to trace the path from the final artifact back to the original source.

**Solution:** Two mandatory attributes are stored for every artifact. "Source" — an immutable identifier of the reference content from which the artifact was generated. "Basis" — the identifier of the operation or document that triggered the change. When an artifact is handed off to the next agent, the Source is copied unchanged and the Basis is updated. Additionally: for every chunk in memory and every generated artifact, the identifier of the model version that performed the generation is stored. All computed projections contain a reference to a specific record in the ground-truth layer.

**Example:** A QA agent receives a task to test a feature. It opens the test case and sees a reference to the technical specification (Basis). From the technical specification, it navigates to the functional requirements (Source of the TS). From the functional requirements — to the original User Story. In this way, when a bug is discovered, the QA agent is able to determine at which stage the original requirement arose and relay an accurate diagnosis back into the pipeline.

**Experimental Verification:** Take a complex artifact and deliberately decompose it into several child artifacts. Verify that each child artifact retains a correct reference to the original. Perform a reverse traversal: from the leaf artifact to the root source. Success: complete traceability with no chain breaks.

**Application History:** Not applied. This section is populated based on real-world use of the pattern: task context, what worked, what required adjustment, and final conclusions.
