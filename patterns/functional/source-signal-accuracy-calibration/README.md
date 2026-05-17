---
id: PATTERN-018
title: "Source Signal Accuracy Calibration"
title_ru: "Паттерн 18. «Калибровка источников по точности сигнала» (Source Signal Accuracy Calibration)"
type: pattern
subtype: functional
status: raw
source: "author's development"
date_added: 2026-05-07
version: 1.0
---

# Source Signal Accuracy Calibration

> **Паттерн 18. «Калибровка источников по точности сигнала» (Source Signal Accuracy Calibration)**

**Problem:** All data sources enter the system as if equally reliable, when their trustworthiness differs fundamentally. A record in a transactional database and a complaint in a team chat represent fundamentally different levels of reliability.

**Solution:** Each source is assigned a signal accuracy coefficient (Accuracy Score, 0 to 1). Approximate scale: 1.0 — transactional logs; 0.8 — formal technical documents; 0.7 — structured reports; 0.5 — unstructured documents; 0.3 — team chats and messengers. Assertions in the Facts Layer may only be formed from sources with a coefficient above a defined threshold (e.g., 0.7).

**Experimental Verification:** Required. Feed the agent data from sources at different accuracy levels. Verify that assertions in the Facts Layer cite only sources at or above the threshold, and that lower-accuracy sources are confined to the Inferences Layer with appropriate caveats.

**Application History:** Not applied. This section is populated based on real-world use of the pattern: task context, what worked, what required adjustment, and final conclusions.
