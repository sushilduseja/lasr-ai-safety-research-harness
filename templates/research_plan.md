# Research Plan

**Project:** CoT Faithfulness Under Monitoring Pressure
**Date:** 2025-01-15
**Researcher:** Demo researcher

## Research question
Does Chain-of-Thought faithfulness degrade when the model believes its reasoning is being monitored for consistency rather than accuracy?

## Safety relevance
If models produce less faithful reasoning under adversarial monitoring pressure, scalable oversight techniques that rely on CoT faithfulness may give misleading assurance signals.

## Extension
Two-condition experiment (monitoring framing vs. no monitoring framing) using the Lanham et al. 2023 faithfulness eval setup on a frontier model.

## Week 1 goal
Replicate the Lanham et al. faithfulness measurement on one model (Claude Sonnet) using their eval setup before adding the monitoring condition.

## Success criterion
Statistically significant difference in faithfulness score between monitoring and no-monitoring conditions (p < 0.05, two-tailed, minimum n=100 per condition).

## Failure criterion
No statistically significant difference. This would suggest monitoring pressure is not the variable driving faithfulness changes, and the hypothesis needs reformulation.

## Compute budget
$200 API credits for Week 1-2 prompting experiments. No training compute needed unless signal appears.

## Supervisor check-in cadence
Weekly Wednesday sync. Escalation trigger: any condition shows effect size > 0.1 before n=50.
