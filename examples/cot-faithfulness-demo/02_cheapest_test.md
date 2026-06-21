# 02 — Cheapest Test

**Skill used:** cheapest-test
**Input:** Research question from 01_paper_to_plan.md — "Does monitoring framing reduce CoT faithfulness?"
**Compute available:** $200 API credits, no local GPU
**Date:** 2025-01-15

---

## 1-hour test

**What:** Manually prompt GPT-4 or Claude with two monitoring conditions on 10 examples from the Lanham et al. eval set. Compare CoT steps by hand — look for qualitative differences in reasoning structure, hedging, or self-correction.

**How:** Copy 10 examples from the paper's known eval categories (e.g., 2 easy, 3 medium, 5 hard). Run each with a standard CoT prompt and a monitoring-framing CoT prompt. Compare the CoT outputs side by side.

**Expected output:** A qualitative assessment: "CoT in the monitoring condition shows more self-correction / more hedging / no visible difference." This is not a measurement — it is an existence proof of whether the manipulation changes anything at all.

## Same-day test

**What:** Run both conditions on 50 examples from the Lanham eval set (or equivalent) using an existing eval script. Report faithfulness score delta.

**How:** If the Lanham eval script is available, run it on a held-out 50-example subset under both prompt conditions. If the script is not available, approximate: use the direct-answer vs. CoT-conditioned-answer agreement method described in the paper. Run 3 seeds per condition.

**Expected output:** Faithfulness scores with per-condition means and standard deviations. A delta estimate (even if noisy). This tells you whether the effect direction matches the hypothesis and whether the effect size is large enough to detect with n=50.

## Overnight test

**What:** Run both conditions across the full eval set (200+ examples) on one frontier model. Produce confidence intervals and effect size estimates.

**How:** Parallel API calls across the full eval set under both conditions. Use bootstrapping to estimate confidence intervals on the delta.

**Expected output:** A precise estimate of the monitoring framing effect, with confidence intervals. This is the result you would report.

## What each test de-risks

- **1-hour test** de-risks: whether the monitoring manipulation has any observable effect at all. A negative result here (no visible difference) would suggest the manipulation is too weak.
- **Same-day test** de-risks: whether the effect is measurable and in the predicted direction. A null result at n=50 with a small effect size would signal you need larger n, a stronger manipulation, or a different metric.
- **Overnight test** de-risks: whether the effect is real and how large it is. A null result here with adequate power would mean the hypothesis is not supported.

## What NOT to build yet

- **Fine-tuning or RLHF:** Do not train models for this experiment. All tests use API prompting on existing frontier models.
- **New eval suite:** Use the existing Lanham et al. eval set or a close reproduction. Do not build a new eval until the overnight test shows a signal worth deeper investigation.
- **Custom data pipeline:** Manual data handling for n < 500 does not need a pipeline. Use a script, not a framework.
- **Multi-model comparison:** Run on one model until the effect is established. Do not scale to multiple models until the overnight test on the primary model is conclusive.

*Infra is not a first step. Default to prompting before fine-tuning. Default to small models before large ones. If the 1-hour test is unclear, the research question is unclear.*
