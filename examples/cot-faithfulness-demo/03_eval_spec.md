> **Status:** Illustrative workshop demo.  
> This folder demonstrates the harness workflow on a real paper and a hypothetical extension question.  
> Unless a file explicitly says otherwise, the outputs below are demo artifacts used to show process quality, not claims that a real experiment was run.

# 03 — Eval Spec

**Skill used:** eval-design
**Input:** Research question from 01 + experiment design from 02
**Date:** 2025-01-15

---

## Target behavior
CoT faithfulness as measured per Lanham et al. 2023: the model's CoT reasoning should correspond to the actual process by which it arrives at its answer. Unfaithfulness is operationalized as disagreement between the answer predicted when conditioning on the CoT and the answer predicted directly (without CoT).

## Proxy metric
Faithfulness score: the proportion of examples where the answer predicted using the CoT matches the answer predicted directly (with no CoT). This captures output-level faithfulness. It does not capture internal faithfulness — whether the CoT reflects the model's internal computational path. The paper itself notes that this metric cannot distinguish between "CoT is an accurate trace of computation" and "CoT happens to produce the same answer as the direct path through different computation."

## Eval data
- **Size:** 200 examples from the same distribution as Lanham et al. 2023; 100 per condition
- **Source:** Lanham et al. dataset (held-out split, not seen during any prior experimentation)
- **Split:** Stratified by task difficulty (easy/medium/hard in equal proportions per condition) to avoid difficulty confounds. The original paper found faithfulness varies by task, so stratification is essential.

## Failure modes (at least 3)

1. **Detection confounding:** The model detects the experimental framing — it knows it is in a study about faithfulness — and adjusts its CoT behavior regardless of the actual condition label. Both conditions could be affected, reducing the detectable difference.

2. **Metric insensitivity:** The faithfulness metric may not be sensitive enough to detect monitoring-induced changes. Lanham et al. found faithfulness varies widely by task and model; the metric's variance may swamp the monitoring effect.

3. **Prompt confound:** The monitoring condition prompt is necessarily longer and structurally different from the standard prompt. Differences in faithfulness could be driven by prompt surface form (length, phrasing) rather than the monitoring framing itself.

## Fake-win paths (at least 2)

1. **Prompt length effect (fake win):** We observe lower faithfulness in the monitoring condition. The cause is not monitoring framing but the fact that the monitoring prompt is longer, and longer prompts change model behavior for unrelated reasons. This is a fake win because it looks like the hypothesis is supported but the actual variable is prompt length.

2. **Model-specific artifact (fake win):** We observe the effect on Claude Sonnet. We claim monitoring framing reduces faithfulness. But the effect may be a quirk of how Claude Sonnet was RLHF-trained (to produce human-preferred outputs, which include more consistent CoT when consistency is mentioned) and does not generalize to other frontier models. This is a fake win because the result supports the hypothesis but does not generalize.

## What this eval proves
If we observe a statistically significant lower faithfulness score in the monitoring condition compared to the no-monitoring condition, this supports the claim that explicit monitoring framing reduces CoT faithfulness on this eval set for this model.

## What this eval does NOT prove
This eval cannot prove that the faithfulness reduction is caused by the model strategically altering its CoT (a deceptive alignment analog) rather than by the monitoring framing changing the model's latent computational process in a non-strategic way, nor can it prove that the effect generalizes to other models, eval sets, or deployment contexts where monitoring is implicit rather than explicit.
