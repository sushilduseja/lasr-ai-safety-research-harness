---
name: cheapest-test
description: >
  Force the fastest informative experiment before any significant infra or training spend. Default to prompting before fine-tuning, small models before large ones.
---

# Cheapest Test

## When to use this
You have a research question and need to design the minimal experiment that reduces uncertainty before committing to expensive infrastructure.

## Inputs required
- Research question or hypothesis
- Available compute (API credits, local GPU, cluster access)
- Any existing eval infrastructure or code repos

## Output format
- 1-hour test: what, how, expected output
- Same-day test: what, how, expected output
- Overnight test: what, how, expected output
- What each test de-risks (one sentence each)
- What NOT to build yet (explicit list)

## Default workflow
1. Design a test that fits in 1 hour using API prompting only.
2. Design a test that fits in one day using available models and scripts.
3. Design an overnight test that requires more compute or parallel runs.
4. State explicitly what failure of each test would mean for the hypothesis.
5. List infrastructure and methods to explicitly defer until signal appears.

## Failure modes
- 1-hour test requires fine-tuning or custom data collection. Simplify until it is purely prompting.
- Same-day test requires new eval construction. Use an existing eval or approximation.
- The user proposes training a model as a first step. Flag and defer.

## AI safety-specific cautions
- AI tools default to suggesting RLHF or fine-tuning because those are common solutions. For cheap tests, prompt-based probes on existing models are almost always faster and more informative.
- "Cheapest test" in an alignment context often means probing an existing frontier model, not training a new one. Bias toward API experiments.

## Prompt block

Copy and paste this into Claude Code or Claude.ai. Replace items in [brackets].

---

I need to design the cheapest informative test for a research question.

**Research question:** [State your research question or hypothesis]

**Available compute:** [e.g., $200 API credits, one A100, cluster of 8 GPUs]

**Existing infrastructure (if any):** [e.g., I have the Lanham eval script, I have a fine-tuning pipeline, nothing yet]

Produce a three-tier experiment ladder:

### 1-hour test
What exactly to run, how to run it (model, prompt, data size), and what output to expect. Must use API prompting on existing models only.

### Same-day test
What to run that takes under 8 hours. May involve running existing eval scripts or processing more data. No new training.

### Overnight test
The first experiment that requires significant compute or parallel runs. Specify what signal from the same-day test justifies running this.

### What each test de-risks
For each of the three tests above, one sentence: "If this test shows [result], we learn that [uncertainty], which means [decision]."

### What NOT to build yet
List specific methods, infrastructure, or training runs to defer. Include: fine-tuning, RLHF, new eval suite development, custom data pipelines. Explain the signal threshold that would justify reconsidering each.

Default to prompting before fine-tuning. Default to small models before large ones. If the 1-hour test is unclear, the research question is unclear.

---
