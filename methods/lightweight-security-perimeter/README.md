---
id: METHOD-002
title: "Lightweight Security Perimeter"
title_ru: "Периметр безопасности на легковесных алгоритмах (Lightweight Security Perimeter)"
type: method
status: raw
subtype: "method / technique"
source: "author's development"
date_added: 2026-05-07
version: 1.0-preview
---

# Lightweight Security Perimeter

> **Периметр безопасности на легковесных алгоритмах (Lightweight Security Perimeter)**

**Problem:** Detecting and masking personally identifiable information (PII) using the LLM itself is unreliable: the model may miss PII or, conversely, falsely flag benign data. Furthermore, transmitting confidential data to the LLM creates a risk of data exfiltration through training processes or request logs.

**Solution:** Before reaching the LLM, the entire incoming data stream passes through a fast detector based on RegEx and small specialized ML models. The detector identifies and masks PII: tax identification numbers (TINs), company names, personal data, and document numbers — replacing them with pseudonyms (COMPANY_001, PERSON_002). The mapping table between pseudonyms and real data is stored separately and is inaccessible to agents. Additionally, Guard Rails are embedded in the RAG pipeline — a document from the knowledge base is served to an agent only if the agent has access rights to that document (verified against the document's attributes and the agent's role).

**Example:** The Requirements Analyst receives a query mentioning a specific company: "The client Romashka LLC has a problem with…" The preprocessor replaces the name: "The client COMPANY_042 has a problem with…" The LLM operates on the pseudonym. The real name is substituted back into the final response. Only COMPANY_042 appears in the LLM request logs.

**Experimental Verification:** Create a test query containing several types of PII: tax identification number (TIN), full name, company name, phone number. Run it through the preprocessor. Verify: real data is absent from LLM request logs, replaced by pseudonyms. Verify completeness: all PII types were intercepted by the detector.

**Application History:** Not applied. This section is populated based on real-world use of the method: task context, what worked, what required adjustment, and final conclusions.

**When to Use:** [Requires author refinement — to be finalized in Phase 4]

**Limitations:** [Requires author refinement — to be finalized in Phase 4]

Related Patterns: [Requires author refinement — to be populated in Phase 4]
