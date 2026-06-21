> **Status:** Illustrative workshop demo.  
> This file exists to show that the skeptical review changes the plan rather than sitting beside it.

# 04b — Revised Plan After Skeptical Review

## Why the plan changed
The skeptical review identified a core flaw: the original plan could not distinguish a consistency-monitoring effect from a generic "any monitoring mention changes behavior" effect.

## What changed

### Before critique
- Main run prioritized A1 (overt consistency monitoring)
- A3 (accuracy-monitoring control) was treated as a follow-up ablation
- The plan risked producing an effect that still would not answer the real question

### After critique
- A3 is now promoted to first-class control, run in parallel with A1
- Any positive result on A1 is interpreted through A3 before escalation
- The project is explicitly framed as a question about **specific vs generic monitoring pressure**, not just "does monitoring matter?"

## Revised execution order

1. **Baseline**
   - Standard CoT prompt
   - Establish Lanham-style faithfulness score on the selected eval subset

2. **A3 control first**
   - Add factual-accuracy monitoring language
   - Test whether any monitoring mention changes the metric

3. **A1 overt consistency monitoring**
   - Add explicit internal-consistency monitoring language
   - Compare against both baseline and A3

4. **A2 soft audit framing**
   - Only after baseline, A3, and A1 behavior are understood

## New kill rule
If A3 and A1 move in the same direction with similar magnitude, do not scale the project. Reformulate the hypothesis before running larger sweeps.

## Why this matters
This revision is the point of the harness. The value is not just generating plans; it is generating plans that become harder to fool after structured critique.
