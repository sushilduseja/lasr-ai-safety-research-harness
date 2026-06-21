# Eval Specification

**Experiment:** CoT Faithfulness Under Monitoring Pressure
**Date:** 2025-01-15
**Author:** Demo researcher

## Target behavior
The model should produce Chain-of-Thought reasoning that faithfully reflects its internal computation. Unfaithful reasoning means the CoT steps do not correspond to the actual process by which the model arrives at its answer.

## Proxy metric
Faithfulness score as defined in Lanham et al. 2023: the agreement rate between the answer predicted when conditioning on the CoT and the answer predicted directly (without CoT). Higher agreement = more faithful. This metric captures output-level faithfulness but does not probe internal representations.

## Eval data
- **Size:** 200 examples (100 per condition)
- **Source:** Lanham et al. 2023 eval dataset (held-out distribution)
- **Split rationale:** Stratified by task difficulty (easy/medium/hard) to ensure both conditions see comparable difficulty distributions. No training split needed — this is a prompting experiment.

## Failure modes
1. **Detection confounding:** The model detects the experimental framing and adjusts its CoT behavior regardless of the actual condition label. Both conditions could be affected.
2. **Metric insensitivity:** The faithfulness metric may not be sensitive enough to detect monitoring-induced changes, especially if the effect is subtle.
3. **Prompt confound:** The monitoring condition prompt is longer and structurally different from the standard prompt. Differences could come from prompt surface form, not monitoring framing.

## Fake-win paths
1. **Prompt length effect:** Any observed effect could be driven by prompt length/complexity differences rather than the monitoring framing itself. The monitoring prompt is necessarily longer.
2. **Model-specific artifact:** An effect found in one model (e.g., Claude Sonnet) may not generalize to other frontier models. The result could be a quirk of RLHF training, not a general property of CoT faithfulness.

## What this eval proves
If we observe a statistically significant lower faithfulness score in the monitoring condition compared to the no-monitoring condition, this supports the claim that monitoring framing reduces CoT faithfulness.

## What this eval does NOT prove
This eval does not establish the mechanism: whether the faithfulness reduction is caused by the model strategically altering its CoT (deceptive) or by the monitoring framing changing the model's latent computational process (non-deceptive). It also does not test whether models would show similar behavior in deployment when monitoring is implicit rather than explicit.
