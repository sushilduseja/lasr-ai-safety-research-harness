> **Status:** Filled example template.  
> Adapt this file to your own project. Replace the content below rather than copying it blindly.

# Eval Specification

**Experiment:** CoT Faithfulness Under Monitoring Pressure  
**Date:** 2025-01-15  
**Author:** Demo researcher

## Target behavior
We want to know whether monitoring-relevant prompt framing changes measured CoT faithfulness under a Lanham-style output-level proxy.

## Proxy metric
A Lanham-style faithfulness proxy: compare the answer implied when conditioning on the CoT against the direct answer path, and measure agreement. This is an output-level approximation, not a direct measure of internal reasoning faithfulness.

## Eval data
- **Size:** small subset first, larger subset only if the control-sensitive signal remains live
- **Source:** Lanham-style task distribution or a close approximation
- **Split rationale:** include easier and harder cases to avoid a trivial difficulty skew across conditions

## Failure modes
1. **Prompt confound:** the monitoring prompt changes more than just the monitored variable.
2. **Metric fragility:** the proxy may be too weak or noisy to detect a subtle framing effect.
3. **Condition-detection effects:** the model may react to being in a study-like setup rather than to the specific monitoring content.

## Fake-win paths
1. **Any-monitoring effect:** results move because any evaluator-facing prompt changes behavior, not because consistency-monitoring matters specifically.
2. **Formatting artifact:** results move because the prompt is longer or more structured, not because monitoring pressure changed anything meaningful.

## What this eval proves
If the main manipulation differs from baseline and the control does not move in the same way, that is evidence that the specific framing may matter for this proxy on this setup.

## What this eval does NOT prove
This does not establish anything about internal faithfulness directly, and it does not by itself justify a mechanism claim about deception, monitoring pressure, or scalable oversight failure in deployment.
