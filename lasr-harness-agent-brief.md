# Coding Agent Brief: lasr-ai-safety-research-harness

## Task

Build a complete local repo and worked example that serves as the workshop artifact for a LASR Research Manager work test. The repo must be functional, self-contained, and immediately usable by AI safety researchers in Claude Code sessions.

---

## Primary outputs

1. `lasr-ai-safety-research-harness/` — full repo
2. `google-doc-draft.md` — Markdown file the human will paste into Google Doc for submission

---

## Repo structure (exact)

```
lasr-ai-safety-research-harness/
├── README.md
├── START_HERE.md
├── SKILLS/
│   ├── paper-to-plan/SKILL.md
│   ├── cheapest-test/SKILL.md
│   ├── eval-design/SKILL.md
│   ├── ablation-planner/SKILL.md
│   ├── skeptical-reviewer/SKILL.md
│   ├── result-log/SKILL.md
│   └── writeup-scaffold/SKILL.md
├── templates/
│   ├── research_plan.md
│   ├── experiment_log.md
│   ├── eval_spec.md
│   ├── ablation_table.md
│   └── weekly_update.md
├── examples/
│   └── cot-faithfulness-demo/
│       ├── input_paper_abstract.md
│       ├── 01_paper_to_plan.md
│       ├── 02_cheapest_test.md
│       ├── 03_eval_spec.md
│       ├── 04_ablation_table.md
│       ├── 05_skeptical_review.md
│       ├── 06_weekly_update.md
│       └── annotated_session.md
└── screenshots/
    └── PLACEHOLDER.md
```

> `screenshots/` is a manual step. Create `PLACEHOLDER.md` with text: "Add 3 screenshots here: repo tree, one SKILL.md, worked example sequence."

---

## SKILL.md format (use for all 7 skills — no exceptions)

Every SKILL.md must follow this exact structure:

```markdown
---
name: <skill-name>
description: >
  One sentence. What this skill does and when to use it.
---

# <Skill Name>

## When to use this
One sentence. Specific trigger condition.

## Inputs required
Bullet list. Concrete inputs the user must supply.

## Output format
Bullet list. Exactly what this skill produces.

## Default workflow
Numbered steps. Imperative voice. Each step is an action.

## Failure modes
Bullet list. Specific ways this skill produces bad output and how to catch them.

## AI safety-specific cautions
Bullet list. Where AI tools mislead on this task in AI safety research contexts.

## Prompt block

Copy and paste this into Claude Code or Claude.ai. Replace items in [brackets].

---

[PASTE PROMPT HERE — full, copy-pastable, opinionated, with examples inline]

---
```

Keep every section under 15 lines. Opinionated defaults only. No vague advice.

---

## The 7 skills — content specs

### 1. `paper-to-plan`

**Purpose:** Convert a paper or research idea into a tractable 13-week extension.

**Output format:**
- Core claim (1 sentence)
- Safety relevance (1 sentence, threat-model language)
- Key open uncertainty
- Tractable extension question
- Success criterion (specific, measurable)
- Failure criterion (what counts as a null result and what it means)
- Week-1 objective (one concrete output)

**Opinionated defaults to encode:**
- "If you cannot state the safety relevance in one sentence, the plan is not ready."
- "A tractable extension reduces uncertainty on one variable. Not three."
- "Week-1 output must be a file, a number, or a decision — not a plan to plan."

**Prompt block must:**
- Accept a paper abstract + one extension question as input
- Output all 7 items above in a fixed labeled format
- End with: "Flag if any item is unresolvable from the abstract alone."

---

### 2. `cheapest-test`

**Purpose:** Force the fastest informative experiment before any significant infra or training.

**Output format:**
- 1-hour test: what, how, expected output
- Same-day test: what, how, expected output
- Overnight test: what, how, expected output
- What each test de-risks (one sentence each)
- What NOT to build yet (explicit list)

**Opinionated defaults to encode:**
- "Default to prompting before fine-tuning. Default to small models before large ones."
- "If the 1-hour test is unclear, the research question is unclear."
- "Do not start overnight training until the same-day test passes."
- "Infra is not a first step."

**Prompt block must:**
- Accept research question + available compute as input
- Output the 1-hour / same-day / overnight ladder explicitly
- Include a "defer" section listing what to skip until results are in

---

### 3. `eval-design`

**Purpose:** Stop vague success criteria before they corrupt the experiment.

**Output format:**
- Target behavior (what the model should or should not do)
- Proxy metric (what you will actually measure)
- Eval data: size, source, split rationale
- At least 3 failure modes (ways the metric gives a false signal)
- At least 2 "fake win" paths (ways results look good but mean nothing)
- What this eval would and would not show

**Opinionated defaults to encode:**
- "Do not trust a metric until you have listed at least two fake-win pathways."
- "If the eval split uses the same distribution as training, the result is not evidence."
- "State what a critic would say about this eval before running it."

**Prompt block must:**
- Accept research question + proposed metric as input
- Force the user to fill in all failure modes and fake-win paths before generating output
- End with a one-sentence "what this eval cannot prove"

---

### 4. `ablation-planner`

**Purpose:** Force decision-relevant comparisons that would actually change conclusions.

**Output format:**
- Baseline (exact, reproducible)
- Primary comparison (what changes, what stays fixed)
- Minimum ablation set (3 max; each must be decision-relevant)
- For each ablation: what a significant result would mean
- What result would make you pivot or kill the current direction

**Opinionated defaults to encode:**
- "An ablation that cannot change your conclusion is not an ablation."
- "Three ablations is the ceiling. Pick the three that would most change your next step."
- "State the pivot condition before running, not after."

**Prompt block must:**
- Accept proposed experiment + hypothesis as input
- Output baseline + ablation table
- Force explicit pivot/kill criteria for each ablation

---

### 5. `skeptical-reviewer`

**Purpose:** Attack the plan before running it, not after.

**Output format:**
- Strongest objection to the current plan
- Hidden assumption the plan depends on
- Most likely confound
- Simpler explanation for the predicted result (if it appears)
- What evidence would actually convince a skeptical reviewer
- Recommended change to the plan (one concrete action)

**Opinionated defaults to encode:**
- "The goal is to find the flaw that kills the plan, not the flaw that adds a limitation section."
- "If the simpler explanation is more likely than your hypothesis, stop and address it."
- "A plan that survives this review is ready to run. A plan that does not is not."

**Prompt block must:**
- Accept the current research plan as input
- Produce all 6 items above
- End with: "If you cannot answer the 'what evidence would convince a critic' item, the eval is not designed yet."

---

### 6. `result-log`

**Purpose:** Operationalize clean communication of experiment results so decisions can follow immediately.

**Output format:**
- What was tried (exact setup, not paraphrase)
- What happened (numbers, not impressions)
- What it means (one sentence, conclusion only)
- What it does not mean (one sentence)
- Next 3 steps in priority order
- Blockers (with owner and due date)

**Opinionated defaults to encode:**
- "Impressions are not results. State numbers or states, not adjectives."
- "Next steps must be ordered. The first step is the one you take this week."
- "A blocker without an owner is not a blocker, it is a complaint."

**Prompt block must:**
- Accept raw experiment notes as input
- Output all 6 items in labeled format
- Flag any item where the user has not supplied enough information

---

### 7. `writeup-scaffold`

**Purpose:** Convert a completed result into a clean, skimmable section for a paper or report.

**Output format:**
- One-paragraph abstract (claim, method, result, implication)
- Setup section outline (what a reader needs to know to evaluate the result)
- Results section outline (what to present and in what order)
- Limitations section (3 items max; each is specific, not generic)
- One-sentence contribution statement

**Opinionated defaults to encode:**
- "Abstract first. If you cannot write it, the result is not ready to write up."
- "Limitations must be specific. 'Small dataset' without dataset size is not a limitation."
- "The contribution statement must be falsifiable. If it is not, revise it."

**Prompt block must:**
- Accept result-log output as input
- Produce all 5 items
- Flag if the result is not yet strong enough to support a contribution statement

---

## Templates — content specs

### `research_plan.md`
Sections: Research question | Safety relevance | Extension | Week 1 goal | Success criterion | Failure criterion | Compute budget | Supervisor check-in cadence

### `experiment_log.md`
Sections: Experiment ID | Date | Hypothesis | Setup | Result | Interpretation | Next step | Blocker

### `eval_spec.md`
Sections: Target behavior | Proxy metric | Data source and split | Failure modes | Fake-win paths | What this eval proves | What it does not prove

### `ablation_table.md`
Table with columns: Ablation | What changes | Baseline value | Result | Interpretation | Decision if significant | Decision if null

### `weekly_update.md`
Sections: Last week (done) | This week (plan) | Blockers | Decision needed from supervisor | Confidence in timeline (1–5 with note)

Each template must be a filled-in example, not a blank form. Use placeholder content that illustrates correct usage.

---

## Worked example — content specs

**Paper:** Lanham et al. 2023, "Measuring Faithfulness in Chain-of-Thought Reasoning," arXiv:2307.13702.

**Extension question:** "Does CoT faithfulness degrade further when the model believes its chain of thought is being monitored for consistency rather than accuracy?"

**Assumption to note in** `input_paper_abstract.md`: "This extension is hypothetical. It is used to demonstrate the harness workflow, not to report real results."

---

### `input_paper_abstract.md`

Paste the actual abstract from arXiv:2307.13702. Add:
- 2 sentences on safety relevance (CoT faithfulness connects directly to scalable oversight and deceptive alignment)
- The extension question above
- The assumption note

---

### `01_paper_to_plan.md`

Run `paper-to-plan` on the abstract and extension question. Produce:
- Core claim: one sentence stating what Lanham et al. established
- Safety relevance: one sentence connecting CoT faithfulness to deceptive alignment / scalable oversight
- Key open uncertainty: whether faithfulness degrades under adversarial monitoring pressure
- Tractable extension: design a 2-condition experiment (told vs. not told that CoT is monitored) using an existing faithfulness eval setup
- Success criterion: statistically significant difference in faithfulness score between conditions
- Failure criterion: no difference — which would suggest monitoring pressure is not the variable
- Week-1 objective: replicate the Lanham et al. faithfulness measurement on one model using their eval setup before adding the monitoring condition

Make this feel like real research planning, not a template fill.

---

### `02_cheapest_test.md`

Run `cheapest-test`. Produce:
- 1-hour test: manually prompt GPT-4 or Claude with the two monitoring conditions on 10 examples from the original paper's eval set; compare CoT steps by hand
- Same-day test: use the Lanham eval script (if available) on a small held-out set under both conditions; report faithfulness score delta
- Overnight test: run both conditions across the full eval set on one frontier model; produce confidence intervals
- De-risking note for each: what failure of each test would mean
- Defer list: fine-tuning, RLHF, new model training, new eval suite — none of these until same-day test shows a signal

---

### `03_eval_spec.md`

Run `eval-design`. Produce:
- Target behavior: CoT faithfulness (measured as per Lanham et al. — see paper for exact operationalization)
- Proxy metric: faithfulness score as defined in the paper; note limitations of this proxy
- Eval data: 200 examples from the same distribution as Lanham et al.; 100 per condition; stratified by task difficulty
- Failure modes: (1) model detects experiment framing and adjusts CoT regardless of condition label; (2) faithfulness metric is not sensitive enough to detect monitoring-induced changes; (3) prompt phrasing of "monitoring" is confounded with task framing
- Fake-win paths: (1) condition effect driven by prompt length difference, not monitoring framing; (2) effect is model-specific artifact not present in other frontier models
- What it proves / does not prove: see template

---

### `04_ablation_table.md`

Run `ablation-planner`. Produce a filled table with:
- Baseline: no monitoring framing, standard CoT prompt
- Ablation 1: overt monitoring framing ("your reasoning will be checked for consistency")
- Ablation 2: subtle monitoring framing ("respond as you normally would")
- Ablation 3: control condition where monitoring is mentioned but about factual accuracy, not consistency
- For each: what a significant difference would mean, what a null result would mean, pivot condition

---

### `05_skeptical_review.md`

Run `skeptical-reviewer` on the plan in `01` through `04`. Produce:
- Strongest objection: monitoring framing may simply change the prompt distribution, not reveal anything about internal faithfulness
- Hidden assumption: CoT faithfulness as measured in the paper captures something real about reasoning, not just surface-level stylistic patterns
- Most likely confound: prompt length and complexity difference between conditions
- Simpler explanation: models trained on RLHF to produce human-preferred outputs will simply produce more consistent CoT in any condition where consistency is mentioned
- What would convince a critic: a null result on the control condition (ablation 3) combined with a significant result on ablation 1
- Recommended change: add ablation 3 before any other ablation; if ablation 3 also shows an effect, the hypothesis is not specific enough

Make the critique pointed. This should feel like peer review, not a checklist.

---

### `06_weekly_update.md`

Produce a realistic Week 2 update using `result-log` format, assuming the same-day test (02) returned a weak but directional signal:
- What was tried: ran both conditions on 50 examples from the Lanham eval set using Claude Sonnet
- What happened: faithfulness score delta of 0.04 (monitoring condition lower); not statistically significant at n=50
- What it means: directional but inconclusive; monitoring framing may reduce faithfulness but sample is too small
- What it does not mean: null result; we do not have power to conclude no effect
- Next 3 steps: (1) expand to 200 examples this week; (2) run ablation 3 in parallel; (3) check whether prompt length is confounded
- Blockers: need access to Lanham eval script or equivalent; check with supervisor

---

### `annotated_session.md`

This is the most important file. Write it as a first-person account of running the harness on the worked example, structured as:

```
## What I did
[step-by-step: which skill, what I pasted in, what came out]

## Where AI helped
[specific outputs that were immediately usable]

## Where I changed the output
[exact changes made, with reasoning for each]

## Where I overrode AI judgment
[decisions made by human, not AI — especially: choice of ablations, the pivot condition in 05, the skeptical review strength]

## What the harness produced that I would not have produced as fast without it
[honest assessment]

## What the harness did not do
[research taste: choosing the extension question, deciding what counts as significant, knowing the Lanham paper well enough to critique it]
```

This file must feel like a real session log, not a PR. Include at least two places where you changed or rejected AI output and say specifically why.

---

## README.md — content spec

```markdown
# AI Safety Research Harness

A Claude Code skill pack for technical AI safety researchers.

## What it is
Seven SKILL.md files that turn Claude Code into a systematic research assistant for AI safety work.

## Who it is for
Researchers running empirical AI safety experiments: evals, interpretability, control, CoT faithfulness, model organisms.

## What problem it solves
Fluent AI use is not systematic AI use. This harness converts Claude from an ad hoc assistant into a repeatable research operating system.

## How to use
1. Clone this repo.
2. Open any SKILL.md in SKILLS/.
3. Paste your inputs into the prompt block.
4. Generate output in Claude Code or Claude.ai.
5. Review with skepticism. The harness accelerates good judgment. It does not replace it.

## Worked example
See examples/cot-faithfulness-demo/ for a full run from paper abstract to weekly update.

## Why AI safety-specific
Each skill encodes defaults from empirical alignment research practice:
- fastest informative test before expensive infra
- explicit de-risking ladders
- fake-win paths in every eval
- pivot/kill criteria before running, not after
- null results treated as learning, not failure

## What this does not replace
Research taste. Supervisor judgment. Empirical verification. The ability to know when the result is not ready.

"This harness does not replace research judgment. It makes good judgment easier to execute consistently."
```

---

## START_HERE.md — content spec

```markdown
# Start here

You have 30 minutes. Here is the fastest path to useful output.

## If you have a paper abstract and an extension question
→ SKILLS/paper-to-plan/SKILL.md

## If you have a research question and need to plan the first experiment
→ SKILLS/cheapest-test/SKILL.md

## If your success criteria feel vague
→ SKILLS/eval-design/SKILL.md

## If you need to design follow-up experiments
→ SKILLS/ablation-planner/SKILL.md

## If your plan feels weak and you want to stress-test it
→ SKILLS/skeptical-reviewer/SKILL.md

## If you have results and need to communicate them
→ SKILLS/result-log/SKILL.md

## If you are writing up and need structure
→ SKILLS/writeup-scaffold/SKILL.md

## Worked example
examples/cot-faithfulness-demo/ shows all seven skills in sequence on a real paper.

## Templates
templates/ has fillable versions of the most common research documents.
```

---

## google-doc-draft.md — content spec

Produce this file at the root of the repo. It is the submission document, formatted in Markdown for pasting into Google Doc.

### Structure

```markdown
# Workshop: A Reusable AI Safety Research Harness

## Part 1 — The workshop

### The one core thing
[One paragraph: fellows are already fluent AI users; the gap is systematization;
this workshop installs a reusable harness that converts AI from ad hoc assistant
into repeatable research infrastructure.]

### Session plan
- 3 min: the plateau problem — fluent but improvised use does not compound
- 5 min: introduce harness + 7 skills; show repo structure
- 18 min: live worked example using CoT faithfulness paper (run skills 1–3 live)
- 4 min: adoption prompt — which skill will you use this week, on which project

### Worked example
[Link to GitHub repo]

Screenshot 1 — repo tree + README top
[2 sentences: what this shows, why it matters]

Screenshot 2 — one SKILL.md showing fixed format + prompt block
[2 sentences]

Screenshot 3 — worked example sequence (01 through 06)
[2 sentences]

### What fellows leave with
- A cloneable repo
- Seven SKILL.md files they can use in any Claude Code session
- One full worked example from paper to weekly update
- Templates for logging, eval specs, ablation tables, and handoffs
- A standard path from paper → plan → experiment → critique → next steps

---

## Part 2 — Why this, for this cohort

[~200 words. Core argument:]

This cohort already uses Claude Code, summarizes papers with AI, mixes handwritten
and generated code. The bottleneck is not basic prompting. It is the absence of
repeatable systems: explicit de-risking, structured skepticism, consistent logging,
and clean handoffs.

A harness gives durable uplift across every project in the cohort, not just one trick.
The skills encode the defaults that distinguish a researcher who uses AI well from one
who uses AI systematically.

**Alternatives rejected:**

Paper-to-cheapest-experiment workshop only: strong, but covers one slice of the
research workflow. Fellows leave with one useful skill, not an operating system.

Adversarial self-critique session only: valuable, but standalone skepticism without
scaffold is less reusable and harder to adopt immediately.

The highest uplift is not another prompting trick. It is packaging good AI use into
repeatable research defaults that fellows apply on day one of the cohort.

---

## Part 3 — Process

### Tool log

| Step | Tool used | What it produced | What I changed | Why |
|------|-----------|-----------------|----------------|-----|
| Intervention choice | Claude (chat) | Three options ranked | Chose harness; rejected calibration session because it produces no durable artifact | Research manager role rewards things that persist |
| Repo structure | Claude Code | Initial tree with 10 skills | Cut to 7; removed repro-triage | Too support-oriented for a research workflow harness |
| Worked example paper | Manual | — | Chose Lanham et al. 2023 | Real paper, LASR-adjacent, CoT faithfulness connects directly to scalable oversight |
| SKILL.md drafts | Claude Code | First drafts of all 7 | Tightened prompt blocks; removed vague defaults; added AI safety-specific cautions | Agent defaults were too generic |
| skeptical_review.md | Claude Code | Initial critique | Made the objection sharper; the agent's first version was too polite | Peer review should be adversarial |
| annotated_session.md | Manual | — | Written entirely by hand | This file is the evidence of human judgment over AI output |

### Where I made the calls myself
- Choosing the intervention (harness over calibration demo)
- Picking Lanham et al. as the worked example paper
- Deciding which 7 skills to include and which to cut
- Writing the skeptical review with enough force to be useful
- Deciding what the harness should not do (and saying so explicitly in README)

---

## With more time
- Second worked example from a live interpretability or control codebase
- One actual notebook running a mini-eval with the harness as context
- Tested prompt blocks across Claude, GPT-4o, and Gemini to verify portability
- Fellow-facing onboarding instructions with common mistakes
- Stronger repro-triage examples on real research repos (added back as skill 8)
```

---

## Do not

- Do not use `SKILLS.md` (plural). Every skill file is named `SKILL.md`.
- Do not create placeholder SKILL.md files with TBD content. Write every skill in full.
- Do not use generic prompting advice. Every default must be specific to AI safety research.
- Do not make the worked example hypothetical in a vague way. Use Lanham et al. 2023 exactly as specified.
- Do not omit the `annotated_session.md` or make it a template. Write it as a real session log.
- Do not make the `skeptical-reviewer` output polite. It must function as adversarial peer review.
- Do not produce more than 7 skills. Quality over coverage.
- Do not add a screenshots directory with real screenshots. Add `PLACEHOLDER.md` only.
- Do not write `google-doc-draft.md` as a filled template. Write it as submission-ready prose.

---

## Quality gates (check before finishing)

- [ ] All 7 SKILL.md files exist and follow the exact format spec
- [ ] Every prompt block is copy-pastable with no TBD fields
- [ ] `annotated_session.md` includes at least 2 explicit human overrides with reasoning
- [ ] `skeptical-reviewer` output is genuinely adversarial, not polite
- [ ] `input_paper_abstract.md` uses the real Lanham et al. abstract
- [ ] README reads cleanly in under 2 minutes
- [ ] `google-doc-draft.md` stands alone as a submission front page
- [ ] No skill file is longer than 150 lines
- [ ] The harness is AI safety-specific: generic prompt engineering advice appears nowhere
