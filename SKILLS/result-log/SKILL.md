---
name: result-log
description: >
  Operationalize clean communication of experiment results so decisions can follow immediately. Numbers, not impressions. Ordered next steps.
---

# Result Log

## When to use this
You have experiment results (raw notes, numbers, observations) and need to communicate them clearly for decision-making.

## Inputs required
- Raw experiment notes (setup, results, observations)
- Blocker information (if any)

## Output format
- What was tried (exact setup, not paraphrase)
- What happened (numbers, not impressions)
- What it means (one sentence, conclusion only)
- What it does not mean (one sentence)
- Next 3 steps in priority order
- Blockers (with owner and due date)

## Default workflow
1. Record the exact setup: model, prompt, data, hyperparameters, seed range. No paraphrases.
2. Report results as numbers or categorical states. No adjectives ("good," "promising," "poor").
3. State the conclusion in one sentence: what this result tells you about your hypothesis.
4. State what this result does NOT tell you: what a critic would correctly say is still unknown.
5. List the next three steps, ordered by priority. The first step is the one you take this week.
6. List blockers. Each must have an owner and a due date.

## Failure modes
- Results described with adjectives instead of numbers. Reject and ask for the actual values.
- Next steps are not ordered. Force a priority order.
- Blocker listed without an owner. Flag — a blocker without an owner is a complaint, not a blocker.

## AI safety-specific cautions
- AI tools tend to summarize results in narrative form ("the model seemed to..."). Strip the narrative. Demand exact numbers and configurations.
- In alignment research, results that look unexciting (null results, small effect sizes) are often the most informative. Do not let the log frame them as disappointing.
- Blocker descriptions in safety research often involve access dependencies (model weights, compute, data). Make ownership explicit — vague blockers stall projects.

## Prompt block

Copy and paste this into Claude Code or Claude.ai. Replace items in [brackets].

---

I have experiment results and need to log them cleanly. Here are my raw notes:

```
[Paste your raw experiment notes — include setup, numbers, observations]
```

Produce a result log with these six sections:

### What was tried
Exact setup. Model name and version, prompt template (not paraphrase), data size and source, hyperparameters, seed range. Someone should be able to replicate from this description.

### What happened
Numbers. Report the actual metric values, confidence intervals, effect sizes. If you compared conditions, report the delta and uncertainty. No adjectives. "State numbers or states, not impressions."

### What it means
One sentence. The conclusion you draw from this result. "This result [supports / contradicts / leaves unresolved] the hypothesis that [claim] because [reason]."

### What it does not mean
One sentence. What a critic would correctly say this result does not prove. Be specific.

### Next 3 steps (in priority order)
1. [Step you take this week] — why this first
2. [Step you take next] — why this second
3. [Step you take after] — why this third

### Blockers
For each blocker: what it is, who owns resolving it, and the due date. A blocker without an owner is not a blocker — it is a complaint.

If any section lacks sufficient information, flag it explicitly and state what additional detail is needed.

---
