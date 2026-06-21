> **Status:** Filled example template.  
> Adapt this file to your own project. Replace the content below rather than copying it blindly.

# Weekly Update

**Week:** 2  
**Project:** CoT Faithfulness Under Monitoring Pressure  
**Date:** 2025-01-22

## Last week (done)
- Built a first-pass plan from the paper and extension question
- Designed the cheapest-test ladder
- Wrote the eval spec with explicit fake-win paths
- Added a monitoring control after skeptical review
- Ran a small illustrative subset comparison

## This week (plan)
1. Run the monitoring control before any larger sweep
2. Decide whether the observed directional difference survives the control
3. Only then decide whether expanding scope is worth it

## Blockers
- Need a verified implementation of the Lanham-style metric or a clearly documented approximation. Owner: researcher. Due: next working session.
- Need a stable eval subset definition so later comparisons are actually reproducible. Owner: researcher. Due: next working session.

## Decision needed from supervisor
If the control condition moves in the same direction as the main manipulation, should this line be killed immediately or reframed as a generic monitoring-pressure question?

## Confidence in timeline (1–5 with note)
**3/5** — The next decision is straightforward, but it depends on whether the control comparison meaningfully disambiguates the interpretation.
