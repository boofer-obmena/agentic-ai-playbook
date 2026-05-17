---
id: PATTERN-016
title: "Interpretation Boundary in UI"
title_ru: "Паттерн 16. «Граница интерпретации в интерфейсе» (Interpretation Boundary in UI)"
type: pattern
subtype: functional
status: raw
source: "author's development"
date_added: 2026-05-07
version: 1.0
---

# Interpretation Boundary in UI

> **Паттерн 16. «Граница интерпретации в интерфейсе» (Interpretation Boundary in UI)**

**Problem:** Language models produce a single continuous text that does not separate verified facts from probabilistic interpretations. The user cannot distinguish "this is definitely true, because it's recorded in the logs" from "this is probably true." False confidence leads to flawed decisions.

**Solution:** Every output artifact is structurally divided into two explicit layers. Facts Layer: assertions backed by ground-truth facts — each fact includes a source reference. Inferences Layer: interpretations, hypotheses, probabilistic assessments — each inference is accompanied by a Confidence Score (0 to 1). The interface prohibits "blending" the layers into a single smooth narrative.

**Experimental Verification:** Required. Provide the agent with a mix of verified log data and ambiguous chat messages. Verify that the output clearly separates the two layers, and that no inference appears in the Facts Layer without a source reference.

**Application History:** Not applied. This section is populated based on real-world use of the pattern: task context, what worked, what required adjustment, and final conclusions.
