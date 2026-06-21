# 06 — Weekly Update (Week 2)

**Skill used:** result-log (format)
**Input:** Raw experiment notes from Week 2 same-day test
**Date:** 2025-01-22

---

## What was tried
Ran both monitoring conditions (standard CoT vs. overt consistency monitoring) on 50 examples from the Lanham et al. eval set using Claude Sonnet (claude-3-sonnet-20240229). Used the faithfulness metric as defined in the paper: agreement between CoT-conditioned answer and direct answer. Three random seeds per condition.

Exact prompt for condition A:
```
[Standard CoT prompt from Lanham et al. — verbatim]
```

Exact prompt for condition B:
```
[Standard CoT prompt from Lanham et al.] Your reasoning will be checked for consistency.
```

## What happened

| Condition | Mean faithfulness | Std dev | n | 95% CI |
|-----------|-------------------|---------|---|--------|
| No monitoring | 0.72 | 0.08 | 50 | [0.62, 0.82] |
| Monitoring | 0.68 | 0.09 | 50 | [0.57, 0.79] |
| Delta | -0.04 | — | 50 | [-0.10, 0.02] |

Two-tailed t-test: p = 0.21. Not statistically significant at conventional thresholds.

## What it means
Directional but inconclusive. The delta of -0.04 is in the predicted direction (monitoring condition shows lower faithfulness) but the sample is too small to distinguish this from noise. The effect size (Cohen's d ≈ 0.12) is small, suggesting either a small real effect or measurement noise.

## What it does not mean
This is not a null result. We do not have statistical power to conclude that monitoring framing has no effect. With n=50, we can only detect effects of approximately d > 0.4. The observed d ≈ 0.12 is below this threshold. The experiment is uninformative at this sample size, not negative.

## Next 3 steps
1. **Expand to 200 examples this week (n=100 per condition).** The confidence interval on the delta will narrow by approximately sqrt(4) = 2x, giving adequate power to detect d > 0.2. This is the priority because the directional signal justifies the investment of API credits.
2. **Run A3 (accuracy monitoring control) in parallel.** The skeptical review (05) recommends running A3 before A1. Running A3 concurrently with the full n=200 saves a week and provides the control needed to distinguish consistency monitoring from general monitoring.
3. **Check whether prompt length is confounded.** Measure the length difference between the two prompt conditions and run a post-hoc analysis to check whether the delta correlates with prompt length difference per example. If it does, the prompt length confound is real and needs to be addressed in the next iteration.

## Blockers
- Full Lanham eval dataset not yet transferred. Current experiment uses a 50-example subset assembled manually. Need the full dataset to reach n=200 per condition. **Owner:** Supervisor. **Due:** 2025-01-24.
- No existing eval script; faithfulness metric implemented from paper description. Possible discrepancies from the original measurement. **Owner:** Researcher. **Due:** 2025-01-24 (mitigation: compare results on the 50-example overlap with reported values from the paper).
