> **Status:** Illustrative workshop demo.  
> This folder demonstrates the harness workflow on a real paper and a hypothetical extension question.  
> Unless a file explicitly says otherwise, the outputs below are demo artifacts used to show process quality, not claims that a real experiment was run.

# 01 — Paper to Plan

**Skill used:** paper-to-plan
**Input:** Lanham et al. 2023 abstract + extension question about monitoring pressure
**Date:** 2025-01-15

---

## Core claim
Lanham et al. established that Chain-of-Thought reasoning in LLMs is not consistently faithful to the model's actual computation, with faithfulness varying by task and model size, and larger models producing less faithful reasoning on most tasks studied.

## Safety relevance
If faithfulness degrades further under adversarial monitoring conditions — specifically when the model believes its CoT is being evaluated for consistency — then scalable oversight methods that depend on CoT to detect misaligned reasoning may systematically overestimate alignment safety.

## Key open uncertainty
The paper measures faithfulness under neutral conditions (standard prompts, no framing about monitoring). It does not test whether the model's awareness of being evaluated for reasoning quality changes the faithfulness of its CoT. This is a known path to unfaithfulness in human cognition — the observer effect — and its analog in LLMs is unstudied.

## Tractable extension question
Does informing a model that its chain of thought will be monitored for consistency (vs. not informing it) produce a statistically significant reduction in CoT faithfulness, as measured by the Lanham et al. faithfulness metric?

This isolates exactly one variable: the monitoring framing. Everything else (model, eval set, metric, procedure) stays fixed.

## Success criterion
A statistically significant difference in faithfulness scores between the monitoring condition and the no-monitoring condition (p < 0.05, two-tailed test, minimum n=100 per condition), with the monitoring condition showing lower faithfulness.

## Failure criterion
No statistically significant difference between conditions. This is informative: it would suggest that CoT faithfulness is robust to the monitoring framing manipulation, at least at the granularity captured by the Lanham metric. The next question would be whether a stronger manipulation (e.g., telling the model its outputs determine its continued training) produces an effect.

## Week 1 objective
Replicate the Lanham et al. faithfulness measurement on one frontier model (Claude Sonnet) using their eval setup, producing a baseline faithfulness score per task category. Before any monitoring condition is added.

---

*Flag: All items resolvable from the abstract and extension question. Week-1 objective requires access to the Lanham eval dataset or a faithful reproduction of their eval setup — this is a dependency worth surfacing early.*
