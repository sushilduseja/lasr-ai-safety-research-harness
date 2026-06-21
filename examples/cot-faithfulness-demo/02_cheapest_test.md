> **Status:** Illustrative workshop demo.  
> This folder demonstrates the harness workflow on a real paper and a hypothetical extension question.  
> Unless a file explicitly says otherwise, the outputs below are demo artifacts used to show process quality, not claims that a real experiment was run.

# 02 — Cheapest Test

**Skill used:** cheapest-test  
**Input:** Research question from 01_paper_to_plan.md — "Does monitoring framing reduce measured CoT faithfulness?"  
**Compute available:** $200 API credits, no local GPU  
**Date:** 2025-01-15

---

## 1-hour test

**What:** Manually compare two prompt framings on 10 examples:
- baseline CoT prompt
- overt consistency-monitoring prompt

**How:** Use 10 examples spanning easier and harder cases. Compare outputs side by side for:
- changes in reasoning structure
- hedging
- self-correction
- obvious answer-distribution shifts

**Expected output:** A qualitative answer to one question: does the manipulation visibly change behavior at all?

## Same-day test

**What:** Run a small subset comparison under:
- baseline
- overt consistency-monitoring
- accuracy-monitoring control

**How:** Use a Lanham-style faithfulness proxy on ~50 examples total. Do one clean pass per condition, then estimate the observed delta with a simple bootstrap or resampling-based uncertainty summary. Do not build new infrastructure.

**Expected output:** A first-pass answer to whether:
1. there is any directional signal, and  
2. that signal survives the monitoring control.

## Overnight test

**What:** Only if the same-day test leaves the question live, expand to a larger subset and rerun:
- baseline
- overt consistency-monitoring
- accuracy-monitoring control

**How:** Scale to a larger evaluation set, keep the same prompt structure, and reuse the same metric approximation. The point of the overnight run is not "final significance"; it is to see whether the directional pattern persists after the control structure is in place.

**Expected output:** A tighter estimate of whether the main effect survives the control comparison strongly enough to justify further work.

## What each test de-risks

- **1-hour test** de-risks whether the prompt manipulation visibly changes model behavior at all.
- **Same-day test** de-risks whether any apparent effect is specific enough to survive the monitoring control.
- **Overnight test** de-risks whether the pattern is stable enough to justify a more serious follow-up.

## What NOT to build yet

- **Fine-tuning or RLHF** — not justified before prompt-only probing shows a live question.
- **A new eval suite** — unnecessary before control-sensitive signal exists.
- **A custom data pipeline** — unnecessary at this scope.
- **A multi-model comparison** — premature before one-model behavior is interpretable.
- **A mechanism story** — do not claim internal-faithfulness implications before output-level effects are even stable.

*Infra is not a first step. Prompt-only probing is the default. If the same-day test does not survive the control comparison, do not scale the run.*
