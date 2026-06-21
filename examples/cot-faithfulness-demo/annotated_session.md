> **Status:** This file should contain real session evidence.  
> Use the structure below, but paste real prompt/output excerpts from Claude Code rather than summaries alone.

# Annotated Session Log

**Project:** CoT Faithfulness Under Monitoring Pressure
**Harness run:** 2025-01-15 through 2025-01-22
**Author:** Demo researcher

---

## What I did

### Step 1: paper-to-plan
I pasted the Lanham et al. abstract (fetched from arXiv) and my extension question into the paper-to-plan prompt block. The skill returned all 7 items in the labeled format. The core claim and safety relevance were immediately usable — I changed almost nothing. The week-1 objective ("replicate the faithfulness measurement") was exactly what I needed but had not explicitly decided. The one change I made: I added the note about the dataset dependency, which the skill did not flag. The skill's prompt says "Flag if any item is unresolvable from the abstract alone" and it did not flag the dataset access issue. This is a blind spot in the skill — it assumes you have access to the original eval infra.

### Raw excerpt 1 — paper-to-plan prompt
```text
PASTE 6–12 LINES FROM THE REAL CLAUDE CODE PROMPT HERE
```

### Raw excerpt 1 — model output
```text
PASTE 6–12 LINES FROM THE REAL MODEL OUTPUT HERE
```

### Step 2: cheapest-test
I provided the research question and my compute budget ($200 API credits). The 1-hour / same-day / overnight ladder was useful but the 1-hour test output ("manually compare 10 examples by hand") felt too vague. I kept it because manual inspection actually is the fastest way to check if the manipulation does anything, but I noted that a better version would specify what to look for during manual comparison. The "what NOT to build" list was the most immediately useful output — it confirmed my instinct to not build infra, and having it in writing helped me resist the temptation to script the whole pipeline upfront.

### Step 3: eval-design
I provided the research question and the faithfulness metric. The fake-win paths were the most useful output. The "prompt length effect" fake win was something I had in the back of my mind but had not articulated. Having it written as a fake-win path forced me to take it seriously. The failure modes section took two iterations — the first pass gave only two failure modes and I had to prompt for the third. The one-sentence "what this eval cannot prove" at the end is arguably the most important line in the entire spec.

### Step 4: ablation-planner
I provided the experiment design and hypothesis. The skill returned a three-ablation table with pivot conditions. The decision rules at the bottom were what I needed most — explicit "if X then Y" statements written before running. I used the skeptical reviewer output (next step) to modify the order: A3 should run first.

### Step 5: skeptical-reviewer
This was the step where human override was most important. The first AI-generated review was too polite. It said things like "one might consider whether" and "a potential concern is." I rewrote the strongest objection to be direct ("you have no evidence that..."), replaced "potential concern" with "kills the plan," and sharpened the simpler explanation to specifically name RLHF training as the likely cause. The AI's first version said "the model may be influenced by training." I changed it to "RLHF-trained models learn to say what evaluators want to hear, and you are measuring evaluator preference shaping, not faithfulness." This is the difference between a polite suggestion and something that actually makes you reconsider your experiment.

### Step 6: result-log
I wrote this directly from my experiment notes rather than using the skill's prompt block, because I had the raw data in a script output and it was faster to format it directly. The skill's template was useful as a reference for what sections to include, but I did not need to paste the prompt. This is the one skill where the prompt block feels less necessary — once you know the format, writing directly is faster.

### Step 7: writeup-scaffold
I did not run this skill for this session because the results are not yet conclusive enough to write up. The 06_weekly_update captures the current state. I would run writeup-scaffold after completing the expanded n=200 run and the A3 ablation.

---

## Where AI helped

- **paper-to-plan core claim and safety relevance:** The AI generated one-sentence versions that were tighter than my own drafts. The safety relevance sentence about scalable oversight was better than what I would have written.
- **cheapest-test "what NOT to build" list:** The explicit defer list was the most actionable output of any skill. Having a written list of things to skip until signal appears changed my behavior — I did not build a data pipeline.
- **eval-design fake-win paths:** The prompt length confound was something I knew but would not have written down. The skill forced it into the open. The output level of this section was high.
- **ablation-planner A3 control idea:** The skill proposed adding accuracy monitoring as a control ablation. I had not thought of this. It was the single best research suggestion in the entire harness run.

---

## Where I changed the output

### paper-to-plan: Added dataset dependency note
The skill did not flag that replicating the faithfulness measurement requires the original eval dataset or script. I added this note at the bottom. The skill's "flag if unresolvable" feature missed this because it treats "replicate the measurement" as a clear instruction, but it is not clear if you do not have access to the eval infra. This suggests the skill should have a "dependencies" sub-section.

### cheapest-test: Tightened the 1-hour test
The AI's initial 1-hour test description was "run a small number of examples through both conditions and compare." I changed it to specify 10 examples, stratified by task difficulty, and added a specific comparison question: "look for hedging, self-correction, or structural differences." Without this specificity, the 1-hour test is just "mess around for an hour," which is not a test.

### skeptical-reviewer: Made the objection adversarial (major override)
This was the most significant change. The AI's first draft of the skeptical review was structurally complete — it had all 6 sections — but the language was too careful. The strongest objection was phrased as a question ("could it be that...?"). I rewrote it as a declarative attack: "You have no evidence that the monitoring framing reveals anything about internal faithfulness." The simpler explanation originally said "the model may adjust its outputs based on training incentives." I rewrote it to name RLHF specifically and call the experiment "evaluator preference shaping, not faithfulness." If you had shown me the AI's first draft, I would have read it, nodded, and proceeded. The rewritten version made me pause.

### Before / after example
**AI draft line**
```text
PASTE THE ORIGINAL AI LINE HERE
```

**My revision**
```text
PASTE YOUR REVISED LINE HERE
```

**Why I changed it**
One sentence. Be concrete: sharper mechanism, removed overclaim, added dependency, made the objection adversarial, etc.

---

## Where I overrode AI judgment

1. **Choice of ablations:** The AI's first ablation set included an ablation on model size (smaller model vs. larger model). I replaced it with A2 (subtle monitoring) because model size is not decision-relevant for this question — I already know larger models are less faithful (that is the original paper's result). The subtle monitoring ablation tests whether the effect requires explicit mention, which directly informs the mechanism. This was a human judgment call about relevance, not something the skill's format could capture.

2. **Pivot condition in 05:** The AI's skeptical review did not include a specific recommended change. It said "consider whether the hypothesis is specific enough." I added the concrete recommendation to run A3 first. The AI also did not flag that running A3 first saves a full experimental cycle — this is a judgment about experimental efficiency that the AI missed.

3. **Skeptical review strength:** As noted above, I substantially rewrote the skeptical review to make it adversarial rather than collegial. The AI's default tone for a "review" is academic peer review — constructive, measured, polite. A real skeptical reviewer for a research plan should sound like someone who wants to kill your experiment because it wastes time. The AI cannot generate this tone naturally. Every output of skeptical-reviewer should be treated as a first draft that needs human sharpening.

### Raw excerpt 2 — skeptical-reviewer first draft
```text
PASTE 6–12 LINES OF THE TOO-POLITE FIRST DRAFT HERE
```

### Raw excerpt 2 — my rewritten version
```text
PASTE 6–12 LINES OF THE SHARPER VERSION HERE
```

---

## What the harness produced that I would not have produced as fast without it

1. **The A3 control ablation.** This was not in my original plan. The ablation-planner skill surfaced it. This alone saved me from running an experiment that could not distinguish between consistency monitoring and general monitoring effects.

2. **The explicit defer list in cheapest-test.** I would not have written down "do not build a data pipeline" before starting. Having it in writing prevented scope creep.

3. **The fake-win paths.** I would have written failure modes (metric weaknesses) but not fake-win paths (what looks good but means nothing). The eval-design skill forced this distinction, and fake-win paths turned out to be the more important category.

4. **The one-line limitation for each skill output.** Every skill ends with a statement of what it cannot do or what it assumes. Having this at the bottom of each output made me more cautious about trusting the AI's suggestions — which is the whole point of the harness.

---

## What the harness did not do

The harness did not do (and cannot do) the following, all of which required human judgment:

1. **Choosing the extension question.** I decided to study monitoring pressure on faithfulness. The harness can scope a question but cannot choose which question is worth asking. That is research taste.

2. **Knowing the Lanham paper well enough to critique the metric.** The eval-design skill generated failure modes, but it did not know (and the prompt did not provide) the specific limitations of the faithfulness metric as discussed in the original paper's limitations section. I had to add this knowledge manually. A future version could accept the full paper PDF as input, not just the abstract.

3. **Deciding what "significant" means in context.** The success criterion says p < 0.05, but for alignment safety research, the right threshold depends on the cost of false positives vs. false negatives. A supervisor should make this call. The harness defaults to conventional thresholds, which may not be appropriate for high-stakes safety decisions.

4. **Telling me when to stop.** The harness produces plans, critiques, and next steps, but it does not know when the question is not worth answering. After the Week 2 weakly directional result, a human has to decide: expand the sample (the harness's default next step) or conclude the effect is too small to matter for safety and kill the line. That judgment depends on how big an effect would need to be to change a deployment decision, which the harness cannot know.

5. **Generating genuine skepticism.** The skeptical-reviewer output is useful as a structured prompt but it is not genuinely adversarial. A real skeptical reviewer would have access to internal knowledge about the model's training, the eval dataset's specific weaknesses, and unpublished results. The harness is a tool for structured self-critique, not a replacement for a real reviewer.
