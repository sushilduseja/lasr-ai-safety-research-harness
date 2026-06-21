# Weekly Update

**Week:** 2
**Project:** CoT Faithfulness Under Monitoring Pressure
**Date:** 2025-01-22

## Last week (done)
- Replicated Lanham et al. faithfulness measurement on Claude Sonnet (n=50 per condition)
- Ran both monitoring conditions on the held-out eval split
- Faithfulness score delta of 0.04 (monitoring condition lower), not statistically significant
- Drafted ablation plan for Week 2

## This week (plan)
1. Expand sample to 200 examples (n=100 per condition) to get adequate power
2. Run ablation A3 (accuracy monitoring control) in parallel
3. Check whether prompt length is confounded with condition

## Blockers
- Full Lanham eval dataset not yet accessed. Need dataset transfer or equivalent eval script. Owner: [Supervisor name]. Due: 2025-01-24.

## Decision needed from supervisor
- Should we proceed with A3 in parallel with the full run, or wait for n=200 results first? Parallel saves a week but risks conflating signals.

## Confidence in timeline (1–5 with note)
**3/5** — Dependent on dataset access. If the dataset arrives by Thursday, the expanded run finishes by end of Week 2 and results are ready for Week 3 review.
