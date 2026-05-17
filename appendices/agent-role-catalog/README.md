---
section: roles
title: "Appendix A. Agent System Role Catalog"
title_ru: "Приложение A. Каталог ролей агентной системы"
type: appendix
status: raw
source: "author's development"
date_added: 2026-05-07
version: 1.0
---

# Appendix A. Agent System Role Catalog

> **Приложение A. Каталог ролей агентной системы**

Roles describe the functional responsibilities of agents within a system. They are not tied to a specific business vertical and can be applied in IT automation as well as in sales, finance, or manufacturing automation.

## 2.1. Architects Level

**Information System Architect:** Sees the landscape of all enterprise systems — their integrations, dependencies, and constraints. Makes decisions about automation boundaries.

**Functional Information System Architect:** Owner of a specific system's architecture (e.g., 1C:ERP or CRM). Knows its subsystems, modules, extension points, and standard constraints.

**Workflow Architect (Agent System Architect):** Designs the agent factory: their roles, interaction rules, effectiveness metrics, interpretation boundaries, and autonomy criteria. Responsible for the integrity of the agent pipeline.

**Functional Agent Pipeline Architect:** Composes agents from the library for a specific task, configures prompts and checks, and operates with executable "Idea Files." Works at the level of a concrete project or function.

## 2.2. Production Pipeline

**Requirements Analyst (Intake Agent):** The first point of contact with the human customer. Gathers initial requirements through interviews or analysis of incoming requests. Formalizes User Stories and enriches them with metadata about the source and signal accuracy coefficient.

**Systems Analyst:** Transforms User Stories into structured Functional Requirements (FR). Identifies contradictions and ambiguities. Operates in Query-Time analyst mode — relies on ground-truth facts from the knowledge base, not on the model's own "memory."

**Technical Writer:** Translates FR into a Technical Specification (TS). The TS is treated as a temporary computed projection — not an ideal outline but a synchronization point between the analyst and the developer.

**Software Engineer (Developer Agent):** Decomposes the TS into atomic tasks and implements them in code. Operates strictly within the Tool Manifest — a list of permitted tools with preconditions for each.

**QA Engineer:** Generates test cases based on FR and TS. Every test case is a formalized artifact with the structure: Preconditions → Actions → Expected Result. The verdict is always binary: Passed / Failed.

## 2.3. Management and Control

**Project Manager / Registrar:** Coordinates the pipeline through the Orchestrator. Tracks task and artifact statuses, escalates blocking issues, and generates reports for the human user. Does not make substantive decisions — only manages the flow.

**Financial Controller:** Budgets the project's computational resources. Splits budgets into two pools: Train Pool (periodic retraining and fine-tuning) and Inference Pool (continuous pipeline operation). Blocks the launch of resource-intensive operations without prior budget acceptance.

**Quality Auditor Agent (Meta-Agent):** Observes the pipeline from the outside. Analyzes logs, artifacts, and errors. Identifies systemic problems, detects data drift and "silent degradation." Verifies that computed projections match ground-truth facts. Proposes architectural adjustments to the Architect.

## 2.4. Infrastructure and Support

**DevOps Agent / Server Administrator:** Monitors the state of computational resources (GPU, SSD indices, containers). Manages deployment and model rotation. Restarts services on failure.

**Technical Support — Tier 1:** Intake agent for support requests. Resolves standard issues using the knowledge base without escalation.

**Technical Support — Tier 2:** Diagnostic agent. Receives escalated requests from Tier 1. Analyzes application logs and the functional architecture of systems to find the root cause of the problem.

**Technical Support — Tier 3:** Works jointly with the DevOps Agent on infrastructure and system problems beyond the capabilities of Tier 2.

## 2.5. Security and Quality

**Defender Agent (Anti-Abuse Shield):** Monitors incoming requests and communications for toxicity. Performs self-audits of agent configurations for vulnerabilities. Protects against the "silent catastrophe" — situations where an agent forms unjustifiably confident conclusions from weak or contradictory input data.
