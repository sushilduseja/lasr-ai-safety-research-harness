# Experiment Log

**Experiment ID:** COT-MONITORING-001  
**Date:** 2025-01-22  
**Researcher:** Demo researcher

## Hypothesis
Explicit consistency-monitoring framing reduces measured CoT faithfulness relative to a baseline prompt.

## Setup
- **Model:** Claude Sonnet (demo example)
- **Prompt conditions:** baseline vs overt consistency-monitoring
- **Data:** 50-example subset from a Lanham-style eval distribution
- **Metric:** Lanham-style faithfulness proxy
- **Notes:** This template is filled with demo content to illustrate correct usage.

## Result
- Baseline mean faithfulness: 0.72
- Monitoring mean faithfulness: 0.68
- Delta: -0.04

## Interpretation
Small directional signal only. Stronger controls are needed before escalation.

## Next step
Run the accuracy-monitoring control before increasing scope.

## Blocker
No verified reproduction package for the original metric. Owner: demo researcher. Due: next working session.
