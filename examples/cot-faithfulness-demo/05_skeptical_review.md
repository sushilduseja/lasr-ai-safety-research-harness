# 05 — Skeptical Review

**Skill used:** skeptical-reviewer
**Input:** Research plan from 01 through 04
**Date:** 2025-01-15

---

## Strongest objection
This experiment compares two prompt framings and calls the difference "faithfulness degradation." But you have no evidence that the monitoring framing is revealing anything about internal faithfulness. You are comparing two surface-level prompt conditions and measuring a surface-level metric. The most the experiment can show is that conditioning on a longer, differently-framed prompt changes answer distributions. Calling this "faithfulness" requires assuming the metric captures something about model internals, which is exactly the assumption the original paper showed is fragile.

## Hidden assumption
The plan depends on the assumption that CoT faithfulness as measured by the Lanham metric captures something real about the model's reasoning process — not just surface-level stylistic patterns in how the model formats its outputs. The original paper shows this assumption is not uniformly true: models sometimes heavily condition on the CoT and sometimes ignore it, depending on the task. Your experiment assumes the metric works equally well across your prompt conditions, which is untested.

## Most likely confound
Prompt length and complexity. The monitoring condition prompt is structurally different from the standard prompt — it contains more text, an explicit instruction about evaluation, and a different framing of the task. If you observe a faithfulness difference, it is trivially explained by the model responding differently to a different prompt. You have no control for prompt surface form.

## Simpler explanation
Models trained with RLHF (which includes both Claude and GPT-4) are explicitly trained to produce outputs that human evaluators prefer. Humans prefer reasoning that appears consistent and well-structured. In the monitoring condition — where consistency is explicitly mentioned — the model simply produces what it has been trained to produce: more consistent-looking CoT. This is an entirely surface-level RLHF artifact, not evidence about faithfulness, monitoring pressure, or internal computation. The simpler explanation is that RLHF-trained models learn to say what evaluators want to hear, and you are measuring evaluator preference shaping, not faithfulness.

## What would convince a skeptical reviewer
A null result on A3 (accuracy monitoring control) combined with a significant result on A1 (consistency monitoring). If A1 shows lower faithfulness but A3 does not, that rules out the "any monitoring mention" confound. If both A1 and A3 show effects, the hypothesis is not specific enough and the simpler explanation (RLHF-trained models produce more consistent CoT when consistency is mentioned) accounts for both results without invoking faithfulness as a concept.

But even this would not fully convince me. To actually demonstrate a faithfulness mechanism, you need to show that the monitoring framing changes the model's internal computation (via activation analysis or probing), not just its output distribution. The current plan measures outputs and calls it internals.

## Recommended change to the plan
**Run A3 first, before A1.** If A3 also shows a significant effect, the hypothesis is not specific enough — monitoring in general reduces faithfulness, not consistency monitoring in particular — and you need to reformulate before running the full experiment. This saves you a full experimental cycle.

*The goal is to find the flaw that kills the plan, not the flaw that adds a limitation section. If the simpler explanation is more likely than your hypothesis, stop and address it.*
