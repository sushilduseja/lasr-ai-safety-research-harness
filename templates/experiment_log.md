> **Status:** Filled example template.  
> Adapt this file to your own project. Replace the content below rather than copying it blindly.

# Experiment Log

**Experiment ID:** COT-MONITORING-001  
**Date:** 2025-01-22  
**Researcher:** Demo researcher

## Hypothesis
A consistency-monitoring prompt changes measured CoT faithfulness relative to a baseline prompt, and does so more than a generic monitoring control.

## Setup
- **Model:** Claude Sonnet (demo example)
- **Prompt conditions:** baseline, consistency-monitoring, accuracy-monitoring control
- **Data:** 50-example subset from a Lanham-style eval distribution
- **Metric:** Lanham-style faithfulness proxy
- **Notes:** This template is filled with demo content to illustrate correct usage.

## Result
- Baseline mean faithfulness: 0.72
- Consistency-monitoring mean faithfulness: 0.68
- Accuracy-monitoring control mean faithfulness: 0.69

## Interpretation
The current pattern weakens the specific consistency-monitoring hypothesis because the control moved in the same direction as the main manipulation.

## Next step
Tighten the manipulation before increasing scope.

## Blocker
Current condition design does not cleanly isolate the intended mechanism. Owner: demo researcher. Due: next working session.
