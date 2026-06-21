---
name: writeup-scaffold
description: >
  Convert a completed result into a clean, skimmable section for a paper or report. Abstract first — if you cannot write it, the result is not ready to write up.
---

# Writeup Scaffold

## When to use this
You have completed experiments with logged results and need to structure them into a paper section or research report.

## Inputs required
- Result-log output from the completed experiment
- Research question and hypothesis (from earlier skills)

## Output format
- One-paragraph abstract (claim, method, result, implication)
- Setup section outline (what a reader needs to know to evaluate the result)
- Results section outline (what to present and in what order)
- Limitations section (3 items max; each is specific, not generic)
- One-sentence contribution statement

## Default workflow
1. Write a one-paragraph abstract covering: claim, method, key result, and implication.
2. Outline the setup section: what the reader needs to know to evaluate the result.
3. Outline the results section: what to present and in what narrative order.
4. List at most three specific limitations, each with justification.
5. Write a one-sentence contribution statement that is falsifiable.

## Failure modes
- Abstract cannot be written because the result is not clear. Flag — the result is not ready to write up.
- Limitations are generic ("small dataset" without dataset size, "limited compute"). Require specifics.
- Contribution statement is not falsifiable ("we shed light on..."). Rewrite to make it testable.

## AI safety-specific cautions
- AI tools readily generate plausible-sounding abstracts that claim more than the data supports. Check every claim against the result log.
- In alignment research, the limitations section often omits the most important limitation: that the experimental setup differs from the real deployment scenario in ways that could change the conclusion. Add this explicitly.
- The contribution statement must be falsifiable. If an alignment claim cannot be disproven by experimental evidence, it does not belong in a results section.

## Prompt block

Copy and paste this into Claude Code or Claude.ai. Replace items in [brackets].

---

I have completed an experiment and need to scaffold a writeup. Here are the results:

**Result log:**

```
[Paste your result-log output here]
```

**Research question:** [Original research question]
**Hypothesis:** [Original hypothesis]

Produce the following five items:

### Abstract
One paragraph covering: the claim being tested, the method used, the key result (with number), and the implication for AI safety research. If you cannot write this paragraph, flag explicitly — the result is not ready to write up.

### Setup section outline
What a reader needs to know to evaluate the result. List the essential information in outline form: model, data, evaluation method, key design decisions. Do not include every detail — include what is necessary for a critical reader to assess the methodology.

### Results section outline
What to present and in what order. Start with the primary result, then secondary analyses, then robustness checks. For each item, note what figure or table would support it.

### Limitations section (3 items max)
Specific limitations, each with a justification. "Small dataset (n=50)" is acceptable. "Small dataset" without the number is not. Each limitation must be specific enough that a reader could evaluate its severity.

### Contribution statement
One sentence. Falsifiable. "We show that [claim] under [conditions], which [implication]." If the result is not yet strong enough to support a falsifiable contribution statement, flag it and explain why.

Abstract first. If you cannot write it, the result is not ready to write up. Limitations must be specific. The contribution statement must be falsifiable. If it is not, revise it.

---
