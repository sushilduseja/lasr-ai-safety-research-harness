> **Status:** Illustrative workshop demo built from an actual Claude Code-assisted workflow.  
> The prompt/output excerpts below are abbreviated from the real working session used to produce the demo artifacts in this folder.  
> The purpose of this file is to show where the harness accelerated the work, where it failed, and where human judgment overrode the model.

# Annotated Session Log

**Project:** CoT Faithfulness Under Monitoring Pressure  
**Harness run:** 2025-01-15 through 2025-01-22  
**Author:** Demo researcher

---

## Provenance

This file documents the workflow that produced the demo artifacts in this folder:
- `01_paper_to_plan.md`
- `02_cheapest_test.md`
- `03_eval_spec.md`
- `04_ablation_table.md`
- `05_skeptical_review.md`
- `04b_revised_plan_after_skeptical_review.md`
- `06_weekly_update.md`

The excerpts below are intentionally short, but they are meant to show real session structure rather than post-hoc summary alone.

---

## What I did

### Step 1: paper-to-plan
I pasted the Lanham et al. abstract and the extension question into the `paper-to-plan` prompt block. The skill returned a usable first-pass plan in the right shape. The main value was not originality; it was compression. I got a claim, a safety relevance sentence, a tractable extension, and a concrete week-1 goal in one shot.

### Raw excerpt 1 — paper-to-plan prompt
```text
I have a paper I want to extend.

Abstract:
Large language models perform better when they produce Chain-of-Thought reasoning...
[full abstract omitted here for brevity]

Extension question:
Does CoT faithfulness degrade further when the model believes its chain of thought is being monitored for consistency rather than accuracy?

Available compute:
API credits only

Produce a research plan with these seven items in exact labeled format.
```

### Raw excerpt 1 — first-pass model output
```text
1. Core claim — Lanham et al. show that Chain-of-Thought reasoning is not always a faithful account of the model's actual reasoning process.

2. Safety relevance — If models produce unfaithful reasoning under oversight-relevant conditions, scalable oversight methods that depend on reading CoT may fail to detect unsafe cognition.

3. Key open uncertainty — The paper does not test whether awareness of monitoring changes measured faithfulness.

4. Tractable extension question — Compare measured faithfulness under a standard prompt and a consistency-monitoring prompt while holding model, data, and metric fixed.
```

### Step 2: cheapest-test
I provided the research question and the compute budget. The useful output was not the overnight test; it was the forced 1-hour / same-day / overnight ladder. That reframed the project as "what can I cheaply falsify first?" rather than "what full study should I build?"

### Step 3: eval-design
I provided the research question and the proposed faithfulness metric. The best output here was the fake-win logic. The skill forced me to write down how the result could look positive while meaning almost nothing.

### Step 4: ablation-planner
I provided the experiment design and baseline. The value here was the discipline of limiting the ablation set and tying each ablation to a concrete decision.

### Step 5: skeptical-reviewer
This was the most important step. The first draft had the correct structure but the wrong force. It was too polite. I rewrote it until it sounded like a reviewer trying to kill a weak experiment rather than a collaborator trying to help.

### Step 6: revised plan
After the skeptical review, I changed the experiment order. The point of this repo is not to generate documents. It is to make critique causally change the plan.

### Step 7: result-log
I then used the result-log format to show what a week-2 update would look like if the first pass returned only a weak directional signal.

---

## Where AI helped

- **Compression:** It turned a paper + extension question into a tractable first-pass plan quickly.
- **De-risking structure:** It forced a 1-hour / same-day / overnight ladder rather than a single overbuilt study design.
- **Eval skepticism:** It surfaced fake-win paths early, especially the prompt-framing confound.
- **Ablation discipline:** It made the plan smaller and more decision-relevant.
- **Documentation shape:** It produced artifacts in formats that are reusable in team workflows.

---

## Where I changed the output

### paper-to-plan: added the missing dependency
The first-pass plan did not surface that replicating the measurement depends on access to the original eval dataset or a faithful approximation. I added that note manually because this is exactly the kind of hidden dependency that can make an otherwise sensible plan non-startable.

### cheapest-test: made the 1-hour test concrete
The AI's first-pass version of the 1-hour test was too vague. I tightened it into:
- 10 examples
- stratified by task difficulty
- compare for hedging / self-correction / structural differences

Without that change, the "1-hour test" was really just "look around for a while."

### skeptical-reviewer: made the objection adversarial
The first-pass skeptical review was too soft.

### Before / after example
**AI draft line**
```text
One possible concern is that the monitoring framing may alter the prompt distribution rather than reveal anything about internal faithfulness.
```

**My revision**
```text
This experiment compares two prompt framings and calls the difference "faithfulness degradation," but you have no evidence that the monitoring framing reveals anything about internal faithfulness at all.
```

**Why I changed it**  
The revised version forces the user to confront the core failure mode immediately instead of treating it as a minor caveat.

---

## Where I overrode AI judgment

1. **Choice of ablations**  
   The first-pass ablation logic drifted toward easy-to-measure changes rather than the most decision-relevant control. I prioritized the accuracy-monitoring control because it is what most directly tests whether the main hypothesis is too vague.

2. **Experiment ordering**  
   I changed the order so that the control question is answered earlier. That is a human judgment call about research efficiency, not just document structure.

3. **Skeptical-reviewer tone**  
   I did not accept the default academic-politeness tone. For this kind of workflow, a skeptical review that does not materially threaten the plan is not useful.

### Raw excerpt 2 — first-pass skeptical review
```text
A potential concern is that the monitoring condition may introduce a prompt confound, since the prompt is longer and includes additional framing that could influence the model's response.
```

### Raw excerpt 2 — sharpened version
```text
Prompt length and prompt framing are the most likely confounds here. If you observe a faithfulness difference, the simplest explanation is that the model responded differently to a different prompt, not that you learned anything about internal faithfulness.
```

---

## What the harness produced that I would not have produced as fast without it

1. A compact first-pass plan with explicit safety relevance.
2. A de-risking ladder instead of a single oversized experiment design.
3. A cleaner distinction between failure modes and fake wins.
4. An ablation plan tied to decisions rather than curiosity.
5. A sharper workflow transition from critique to revision.

---

## What the harness did not do

1. It did not choose the extension question. That required research taste.
2. It did not verify that the Lanham-style metric approximation is good enough for real use.
3. It did not tell me whether the question is important enough to pursue after weak signal.
4. It did not replace the need for real empirical verification.
5. It did not generate truly adversarial critique without human sharpening.

## Bottom line

The harness is most useful once the researcher already has a plausible question and wants to move faster without becoming sloppier. Its biggest value is not "better prompting." It is forcing a tighter loop between scope, de-risking, eval design, critique, and next-step selection.

Its biggest weakness is that it does not replace research taste. It can make a weak question more structured, but it cannot make it more important. It also does not remove the need for real empirical verification, especially when the proxy metric is fragile or the mechanism claim is stronger than the observed behavior.
