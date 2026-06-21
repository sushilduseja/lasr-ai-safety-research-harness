> **Status:** Illustrative workshop demo.  
> This folder demonstrates the harness workflow on a real paper and a hypothetical extension question.  
> Unless a file explicitly says otherwise, the outputs below are demo artifacts used to show process quality, not claims that a real experiment was run.

# 01 — Paper to Plan

**Skill used:** paper-to-plan  
**Input:** Lanham et al. 2023 abstract + extension question about monitoring pressure  
**Date:** 2025-01-15

---

## Core claim
Lanham et al. show that Chain-of-Thought reasoning is not uniformly faithful to the model's actual reasoning process, and that faithfulness varies by task and tends to degrade as models become larger and more capable.

## Safety relevance
If faithfulness degrades further under monitoring-relevant prompt framing, scalable oversight methods that rely on reading CoT may produce misleading assurance signals about what the model is actually doing.

## Key open uncertainty
The paper studies faithfulness under neutral prompt conditions. It does not test whether telling the model that its reasoning will be reviewed changes measured faithfulness.

## Tractable extension question
Does adding explicit consistency-monitoring framing to a standard CoT prompt change a Lanham-style faithfulness metric, relative to a baseline prompt and a monitoring control condition?

This isolates one variable: monitoring-relevant framing.

## Success criterion
Observe a stable condition difference that survives the monitoring control and is large enough to justify a larger follow-up.

## Failure criterion
No meaningful difference, or a difference that disappears once the monitoring control is added. In that case, the current framing is not worth scaling as-is.

## Week 1 objective
Produce a baseline measurement and one first-pass de-risking result on a small subset before committing to any larger run.

---

*Flag: The extension question is resolvable from the abstract. A faithful implementation still depends on access to a Lanham-style dataset and metric approximation or reproduction path, which is a real dependency to surface early.*
