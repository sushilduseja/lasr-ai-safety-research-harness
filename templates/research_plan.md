> **Status:** Filled example template.  
> Adapt this file to your own project. Replace the content below rather than copying it blindly.

# Research Plan

**Project:** CoT Faithfulness Under Monitoring Pressure  
**Date:** 2025-01-15  
**Researcher:** Demo researcher

## Research question
Does measured CoT faithfulness change when the model is explicitly told that its reasoning will be reviewed for internal consistency?

## Safety relevance
If monitoring-relevant prompt framing changes measured faithfulness, scalable oversight methods that rely on CoT may produce misleading assurance signals.

## Extension
Prompt-only comparison between:
- a standard CoT condition
- a consistency-monitoring condition
- a monitoring control condition

using a Lanham-style faithfulness metric approximation on one model.

## Week 1 goal
Produce a baseline measurement and a first-pass de-risking result on a small subset before committing to a larger run.

## Success criterion
Observe a stable condition difference that survives the monitoring control and is large enough to justify a larger follow-up.

## Failure criterion
No meaningful difference, or a difference that disappears once the monitoring control is added. In that case, the current framing is not worth scaling as-is.

## Compute budget
API-only for the first pass. No training or custom infrastructure unless early signal survives control checks.

## Supervisor check-in cadence
Weekly sync, with earlier escalation only if the control comparison materially changes the interpretation.
