---
name: skeptical-reviewer
description: >
  Attack the research plan before running it, not after. Finds the flaw that kills the plan, not the flaw that adds a limitation section.
---

# Skeptical Reviewer

## When to use this
You have a complete research plan (paper-to-plan through ablation-planner) and want to stress-test it before running experiments.

## Inputs required
- Current research plan (including research question, experiment design, eval spec, ablations)

## Output format
- Strongest objection to the current plan
- Hidden assumption the plan depends on
- Most likely confound
- Simpler explanation for the predicted result (if it appears)
- What evidence would actually convince a skeptical reviewer
- Recommended change to the plan (one concrete action)

## Default workflow
1. Read the plan and identify the single most damaging objection.
2. Surface the hidden assumption that, if false, collapses the plan.
3. Identify the most plausible confound that would explain results without supporting the hypothesis.
4. Construct a simpler explanation for the predicted result.
5. Define what evidence would be convincing enough to change a skeptic's mind.
6. Recommend exactly one concrete change to the plan.

## Failure modes
- The objection is polite or adds a limitation section rather than challenging the core claim. Rewrite to be adversarial.
- No simpler explanation is offered. Force one — if the simpler explanation is more likely than the hypothesis, stop and address it.
- The "what evidence would convince a critic" item cannot be answered. This means the eval is not designed yet.

## AI safety-specific cautions
- AI tools have a strong politeness bias. The first draft of a skeptical review will almost always be too gentle. Escalate the objection severity.
- In alignment research, the most common hidden assumption is that the model's internal representations correspond to the behavior we observe. Challenge this explicitly.
- AI reviewers tend to accept the premise of the experiment and critique execution. A good skeptical review also questions whether the experiment tests what the author thinks it tests.

## Prompt block

Copy and paste this into Claude Code or Claude.ai. Replace items in [brackets].

---

I need you to act as an adversarial skeptical reviewer for the following research plan. Your goal is to find the flaw that kills the plan, not the flaw that adds a limitation section.

**Research plan:**

```
[Paste your research plan — include research question, experiment design, eval spec, and ablation plan]
```

Produce exactly six items:

### 1. Strongest objection
The single most damaging thing wrong with this plan. Be direct. Do not soften it.

### 2. Hidden assumption
What must be true for this plan to produce valid results? State it explicitly. If this assumption is false, the plan collapses.

### 3. Most likely confound
The most plausible alternative explanation for the predicted results. Be specific about where it enters the experimental design.

### 4. Simpler explanation
If the predicted results appear, what is a simpler explanation than the hypothesis? If this simpler explanation is more likely than your hypothesis, stop and address it before running experiments.

### 5. What would convince a skeptic
What specific evidence would actually change a skeptical reviewer's mind? If you cannot answer this, the eval is not designed yet.

### 6. Recommended change
Exactly one concrete action to address the strongest objection. Not "be more careful" — a specific experimental or design change.

A plan that survives this review is ready to run. A plan that does not is not.

---
