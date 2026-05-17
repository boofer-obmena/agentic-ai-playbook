---
id: METHOD-016
title: "Techniques of Forced Reasoning (CoT, ToT, Self-Consistency)"
title_ru: "Техники принудительного рассуждения (CoT, ToT, Self-Consistency)"
type: method
status: raw
subtype: "method / technique"
source: "Master All 20 Agentic AI Design Patterns (SOURCE-006); Chain-of-Thought Prompting (Google Brain, 2022)"
date_added: 2026-05-11
version: 1.0
related: ["PATTERN-006 (uses)", "PATTERN-017 (uses)", "PATTERN-021 (uses)", "PATTERN-043 (uses)"]
---

# Techniques of Forced Reasoning (CoT, ToT, Self-Consistency)

> **Техники принудительного рассуждения (CoT, ToT, Self-Consistency)**

**Problem:** By default, the LLM generates a response in a single direct pass — from question to answer, with no intermediate steps. On complex tasks (mathematics, multi-step planning, logical analysis, legal reasoning), such an "intuitive leap" leads to a high probability of error. The model "guesses" the answer rather than computing it. At the same time, architectural patterns (Reflection, Debate, Planning) require reasoning-enhancement tools at the level of an individual LLM call — but do not themselves solve the question of how to make the model reason rather than guess.

**Solution:** A family of prompt techniques that force the model to explicitly construct a reasoning chain before producing the final answer. The techniques differ in computational cost, exploration depth, and reliability — the developer selects the technique appropriate to the task class.

---

**Chain-of-Thought (CoT) — linear reasoning.** The model receives a prompt augmented with an instruction to output intermediate steps: "Let's think step by step." Instead of a direct answer, the model sequentially articulates: "Given: … From this it follows that: … Compute: … Check boundary conditions: … Answer: X." Each step builds on the previous one; a logical error becomes visible (and potentially correctable by the model) before the final answer is reached.

CoT is the baseline technique, a single model call. Modern models (Claude, GPT-4) support a built-in thinking mode in which the reasoning chain is generated inside the model and is not shown to the user. CoT improves accuracy at the cost of roughly 2× latency and token consumption for the hidden chain.

**Tree-of-Thoughts (ToT) — branching exploratory reasoning.** The model does not follow a single chain, but at each step generates several continuation options (typically 3–5), evaluates each against a defined criterion, and develops the best one. If a branch reaches a dead end, the model returns to the previous fork and tries an alternative. Analogy: a chess engine evaluating move options with position scoring.

ToT requires multiple sequential model calls: generator → evaluator → selection → continuation. It is significantly more expensive than CoT in latency and tokens, but provides gains on tasks with a large solution space and a non-obvious path to the answer: creative writing, strategic planning, and the search for unconventional architectural alternatives.

**Self-Consistency — statistical stabilization.** The same CoT prompt is run N times (typically 5–7), and the most frequently occurring answer is selected (majority voting). The LLM is probabilistic: across different runs, the same prompt yields slightly different answers. Self-Consistency turns this weakness into a strength — random errors and hallucinations are filtered out by voting; the consensus answer is statistically more robust than any individual result.

Self-Consistency increases cost N-fold, but radically improves accuracy on tasks with a high cost of error. It is orthogonal to CoT and ToT — it can be applied on top of either.

---

**Technique selection rule:**

| Task class | Technique | Trade-off |
|---|---|---|
| Routine factual query | No technique | Minimum cost |
| Logic, mathematics, deduction | CoT | +latency ~2× |
| Open exploration, strategy, creativity | ToT | +latency ~5–10× |
| High cost of error (law, medicine, finance) | CoT + Self-Consistency | +cost ~5× |

**Example:** The analyst agent within PATTERN-021 (Debate) is tasked with: "Which stack to choose for a high-load real-time pipeline under a constrained budget?" Instead of a direct CoT reasoning, ToT is launched: the model generates 3 stack architecture alternatives, evaluates each for latency, cost, and risk, eliminates the clearly non-viable branch, deepens the two remaining ones, compares them, and produces a final recommendation with justification. The result is passed to Debate, where other roles challenge specific aspects of the choice.

**Relationship to Other Entities:** Used by patterns: PATTERN-043 (Reflection) — CoT at the "Critique" step; PATTERN-021 (Debate) — CoT or ToT at the role argumentation step; PATTERN-006 (Planning) — CoT at the plan generation step; PATTERN-017 (Dynamic Ontology) — ToT for exploring semantic connections. Related to PRINCIPLE-011 (Think Mode) — think: true in Claude API terms is an implementation of CoT at the model level.

**Experimental Verification:** Required. Plan: select 3 task classes (logical, creative, high-stakes), for each run 3 modes (direct answer / CoT / ToT + Self-Consistency), measure accuracy and cost. Compare CoT with Claude's built-in thinking mode.

**Application History:** Not applied. This section is populated based on real-world use of the method: task context, what worked, what required adjustment, and final conclusions.
