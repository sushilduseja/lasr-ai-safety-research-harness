---
name: eval-design
description: >
  Stop vague success criteria before they corrupt the experiment. Forces explicit failure modes, fake-win paths, and a statement of what the eval cannot prove.
---

# Eval Design

## When to use this
You have a research question and a proposed metric, but you are not sure the metric actually measures what you care about.

## Inputs required
- Research question or hypothesis
- Proposed metric or evaluation approach
- Available data sources and rough data size

## Output format
- Target behavior (what the model should or should not do)
- Proxy metric (what you will actually measure)
- Eval data: size, source, split rationale
- At least 3 failure modes (ways the metric gives a false signal)
- At least 2 "fake win" paths (ways results look good but mean nothing)
- What this eval would and would not show

## Default workflow
1. Define the target behavior in terms of model inputs and outputs.
2. Choose a specific proxy metric. State what it actually measures vs. what you wish it measured.
3. Specify data size, source distribution, and train/test split rationale.
4. List at least three ways the proxy metric could mislead.
5. List at least two ways results could look positive without supporting the hypothesis.
6. Write one sentence stating what this eval can prove and one stating what it cannot.

## Failure modes
- Fewer than three failure modes listed. The metric is not well-understood yet.
- Fake-win paths listed are implausible. Push for realistic confounds.
- Split rationale is missing or uses training distribution as eval distribution. Flag.

## AI safety-specific cautions
- AI tools tend to produce eval designs that match standard ML benchmarks but miss alignment-specific failure modes (goodharting, specification gaming, reward hacking).
- "Fake-win" paths in alignment evals often involve the model learning to produce human-preferred outputs rather than actually solving the task. Check for this explicitly.
- The proxy metric in alignment evals is almost never the thing you actually care about. The gap between proxy and target is where dangerous failures live.

## Prompt block

Copy and paste this into Claude Code or Claude.ai. Replace items in [brackets].

---

I need to design an evaluation for a research experiment.

**Research question:** [State your research question]

**Proposed metric:** [What you plan to measure and how]

**Available data:** [Rough size, source, any existing splits]

Produce an eval specification with these sections:

### Target behavior
Describe exactly what the model should or should not do. Input → output pairs with examples.

### Proxy metric
What you will actually measure. State the metric, how it is computed, and what it misses about the target behavior.

### Eval data
Size, source distribution, and explicit rationale for how you split train/val/test. If the eval split uses the same distribution as training, explain why that is acceptable or flag it as a limitation.

### Failure modes (at least 3)
Specific ways the metric could give a false signal. For each: what the metric would show, what is actually happening, and why you might not catch it.

### Fake-win paths (at least 2)
Ways the experiment could return positive results that do not actually support the hypothesis. "If we see X, it looks like success but could actually mean Y."

### What this eval proves
One sentence. Concrete. "If we observe [result], we can conclude [claim] because [reason]."

### What this eval does NOT prove
One sentence. What a critic would correctly say this eval fails to show. Do not trust a metric until you have listed at least two fake-win pathways. State what a critic would say about this eval before running it.

---
