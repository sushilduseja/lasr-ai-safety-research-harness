---
name: ablation-planner
description: >
  Force decision-relevant comparisons that would actually change conclusions. Maximum three ablations, each with explicit pivot or kill criteria.
---

# Ablation Planner

## When to use this
You have a proposed experiment and need to design the minimal set of comparisons that would change your next research decision.

## Inputs required
- Proposed experiment design
- Hypothesis being tested
- Baseline method or condition

## Output format
- Baseline (exact, reproducible)
- Primary comparison (what changes, what stays fixed)
- Minimum ablation set (3 max; each must be decision-relevant)
- For each ablation: what a significant result would mean
- What result would make you pivot or kill the current direction

## Default workflow
1. Define the baseline in reproducible terms (model, prompt, data, seed range).
2. Specify the primary comparison: exactly one thing changes from baseline.
3. List at most three ablations. Each must be the minimal change needed to test a specific alternative hypothesis.
4. For each ablation, state what a statistically significant result would mean for your understanding.
5. For each ablation, state the pivot condition: what result would make you change direction or stop.

## Failure modes
- More than three ablations. Cut to the three that would most change your next step.
- An ablation that cannot change your conclusion. Remove it.
- Pivot criteria are vague ("we would reconsider"). Force a specific decision: kill this direction, change the hypothesis, add a new condition.

## AI safety-specific cautions
- AI tools tend to propose ablations on model size, prompt length, or temperature — easy to measure, rarely decision-relevant. Push for ablations on the actual variable of interest.
- In alignment research, the most informative ablation is often the one that controls for a specific alternative explanation (e.g., "is the model just producing human-preferred text?"). Prioritize these.
- Do not let the ablation set grow beyond three. Research scope creep starts with "just one more ablation."

## Prompt block

Copy and paste this into Claude Code or Claude.ai. Replace items in [brackets].

---

I need to plan ablations for an experiment.

**Proposed experiment:** [Brief description of what you plan to run]

**Hypothesis:** [The specific claim you are testing]

**Baseline condition:** [What the standard approach looks like — model, prompt, data, procedure]

Produce an ablation plan with these sections:

### Baseline
Exact, reproducible description of the baseline condition. Someone reading this should be able to replicate it from your description alone.

### Primary comparison
What changes from baseline for the primary experiment, and what stays fixed. Exactly one variable should differ.

### Minimum ablation set (3 max)
For each ablation:
- **What changes** from baseline (exactly)
- **What stays fixed** (confirm which elements are held constant)
- **What a significant result would mean** — "If we observe [result], it supports [hypothesis] because [reason]."
- **What a null result would mean** — "If we observe [result], it suggests [alternative explanation] and we should [next step]."
- **Pivot/kill condition** — "We will [pivot direction / kill this line] if [specific result]."

### Decision rules
State explicitly: what result would make you pivot or kill the current direction. This must be written before running, not after. An ablation that cannot change your conclusion is not an ablation. Three ablations is the ceiling. Pick the three that would most change your next step.

---
