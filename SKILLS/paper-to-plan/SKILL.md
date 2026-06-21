---
name: paper-to-plan
description: >
  Convert a paper or research idea into a tractable 13-week extension plan with explicit safety relevance, success criteria, and a concrete week-1 output.
---

# Paper to Plan

## When to use this
You have read a paper (or have an extension idea) and need to scope a tractable research project before designing experiments.

## Inputs required
- Paper abstract or full paper text
- One specific extension question you want to explore
- Compute budget (rough order: API-only, single GPU, multi-GPU)

## Output format
- Core claim (1 sentence)
- Safety relevance (1 sentence, threat-model language)
- Key open uncertainty
- Tractable extension question
- Success criterion (specific, measurable)
- Failure criterion (what counts as a null result and what it means)
- Week-1 objective (one concrete output)

## Default workflow
1. State the paper's core claim in one sentence.
2. Connect it to a concrete AI safety threat model in one sentence.
3. Identify exactly one open uncertainty the paper leaves unresolved.
4. Frame a tractable extension that isolates one variable.
5. Define what success looks like as a measurable outcome.
6. Define what a null result means and why it is still informative.
7. Specify one concrete week-1 deliverable (a file, a number, or a decision).

## Failure modes
- Plan addresses three variables instead of one. Cut until only one remains.
- Success criterion is not measurable ("better understanding"). Require a number or binary decision.
- Week-1 output is "review the literature" or "write a plan." Reject and reframe.

## AI safety-specific cautions
- AI tools readily generate plausible-sounding plans that are not tractable in 13 weeks. Push back on compute estimates and eval complexity.
- "Safety relevance" sections often drift into advocacy. Stay in threat-model language.
- The extension question must be downstream of the paper's actual results, not a separate idea that the paper merely inspired.

## Prompt block

Copy and paste this into Claude Code or Claude.ai. Replace items in [brackets].

---

I have a paper I want to extend. Here is the abstract:

```
[Paste paper abstract here]
```

My extension question is:

```
[One specific extension question]
```

Available compute (rough order): [API credits / single GPU / multi-GPU cluster]

Produce a research plan with these seven items in this exact labeled format:

1. **Core claim** — One sentence stating what the paper established.
2. **Safety relevance** — One sentence in threat-model language connecting this to an AI safety problem (deceptive alignment, scalable oversight, specification gaming, etc.).
3. **Key open uncertainty** — The one unanswered question from the paper that this extension targets.
4. **Tractable extension question** — A concrete question that isolates exactly one variable and can be answered in 13 weeks.
5. **Success criterion** — A specific, measurable outcome. "We will conclude X if Y happens and not otherwise."
6. **Failure criterion** — What counts as a null result and why it is still informative. "If Z happens, we learn that [assumption] is wrong, which changes [next step]."
7. **Week-1 objective** — One concrete output: a file, a number, or a decision. Not a plan to plan.

For each item, give a direct answer. Do not hedge. If any item is unresolvable from the abstract alone, flag it explicitly and say what additional information you need.

---
