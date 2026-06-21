# Workshop: A Reusable AI Safety Research Harness

## Part 1 — The workshop

### The one core thing

LASR fellows are already fluent AI users. They summarize papers with Claude, write code with Copilot, and debug with GPT-4. The bottleneck is not basic prompting — it is systematization. A fellow who uses AI ad hoc on every project gets a different kind of help each time; a fellow who uses an installed, opinionated harness gets repeatable structure. This workshop delivers exactly that: a seven-skill Claude Code harness that converts AI from an ad hoc assistant into a repeatable research operating system, designed explicitly for empirical AI safety work.

### Session plan

- **3 min:** The plateau problem — fluent but improvised AI use does not compound. Each project starts from scratch. Most fellows already feel this.
- **5 min:** Introduce the harness and its seven skills. Show the repo structure (README, START_HERE, SKILLS/, templates/, examples/). The key design constraint: every skill has a fixed format and a copy-pastable prompt block that encodes AI safety research defaults.
- **18 min:** Live worked example using the CoT faithfulness paper (Lanham et al. 2023, arXiv:2307.13702). Run skills 1–3 live: paper-to-plan on the abstract, cheapest-test on the extension question, eval-design on the proposed metric. Each step produces a concrete artifact. Show the skeptical-reviewer output (pre-written) to demonstrate adversarial self-critique.
- **4 min:** Adoption prompt — each fellow identifies which skill they will use this week and on which project. Commitment is the output.

### Worked example

Full repository: [GitHub link to repo]

**Screenshot 1 — repo tree + README top**
Shows the complete file structure and the opening of README. This demonstrates that the harness is self-contained: a researcher can clone it and immediately navigate from START_HERE to any skill.

**Screenshot 2 — one SKILL.md showing fixed format + prompt block**
Shows the paper-to-plan skill with its seven-section structure and fully pastable prompt at the bottom. This is the core unit of the harness — every skill follows this exact template, which means once you learn one, you know all seven.

**Screenshot 3 — worked example sequence (01 through 06)**
Shows the progression from abstract (input_paper_abstract.md) through plan (01), cheapest test (02), eval spec (03), ablation table (04), skeptical review (05), and weekly update (06). This proves the harness produces a complete research workflow, not isolated artifacts.

### What fellows leave with

- A cloneable GitHub repo
- Seven SKILL.md files they can use in any Claude Code session
- One full worked example from paper abstract to weekly update
- Templates for research plans, experiment logs, eval specs, ablation tables, and weekly updates
- A standard path from paper to plan to experiment to critique to next steps — usable on Monday morning

---

## Part 2 — Why this, for this cohort

This cohort already uses Claude Code, summarizes papers with AI, and mixes handwritten and generated code. The bottleneck is not basic prompting. It is the absence of repeatable systems: explicit de-risking steps before expensive compute, structured skepticism built into the experimental design phase, consistent logging across experiments, and clean handoffs between research phases.

A harness gives durable uplift across every project in the cohort, not just one trick. The seven skills encode the defaults that distinguish a researcher who uses AI well from one who uses AI systematically: fake-win paths in every eval, pivot-or-kill decisions before running, null results treated as learning rather than failure, and fastest informative test before any infrastructure spend.

**Alternatives rejected:**

- *Paper-to-cheapest-experiment workshop only:* Strong as a single session, but covers one slice of the research workflow. Fellows leave with one useful skill, not an operating system they can reuse across projects.

- *Adversarial self-critique session only:* Valuable, but standalone skepticism without scaffolded structure is less reusable and harder to adopt immediately after the workshop.

- *Generic AI productivity workshop:* Does not encode AI safety research norms. The defaults matter — a reproducible eval design skill that omits fake-win paths is not safe to use in alignment research.

The highest uplift for this cohort is not another prompting trick. It is packaging good AI use into repeatable research defaults that fellows apply on day one of the cohort and use on every subsequent project.

---

## Part 3 — Process

### Tool log

| Step | Tool used | What it produced | What I changed | Why |
|------|-----------|-----------------|----------------|-----|
| Intervention choice | Claude (chat) | Three options ranked | Chose harness; rejected calibration session because it produces no durable artifact | Research manager role rewards things that persist |
| Repo structure | Claude Code | Initial tree with 10 skills | Cut to 7; removed repro-triage | Too support-oriented for a research workflow harness; belongs in a companion skill pack |
| Worked example paper | Manual | — | Chose Lanham et al. 2023 | Real paper, LASR-adjacent, CoT faithfulness connects directly to scalable oversight |
| SKILL.md drafts | Claude Code | First drafts of all 7 | Tightened prompt blocks; removed vague defaults; added AI safety-specific cautions | Agent defaults were too generic and did not encode alignment research norms |
| skeptical_review.md | Claude Code | Initial critique | Made the objection sharper; rewrote from polite to adversarial; added specific RLHF critique | Peer review should be genuinely adversarial, not constructive commentary |
| annotated_session.md | Manual | — | Written entirely by hand | This file is the evidence of human judgment over AI output; delegating it would defeat its purpose |

### Where I made the calls myself

- **Choosing the intervention (harness over calibration demo).** A calibration session workshop would produce a one-time behavior change. A harness produces a reusable artifact. For a research manager role, durable artifacts are the right output.
- **Picking Lanham et al. as the worked example paper.** Needed a real paper, LASR-adjacent, with an extension question that is tractable in a workshop demonstration and connects directly to scalable oversight — the core alignment problem the cohort cares about.
- **Deciding which 7 skills to include and which to cut.** The AI proposed 10 skills. I cut repro-triage (too operations-oriented for a research harness), literature-mapper (too broad — every paper tool does this), and data-card-generator (too narrow — belongs in a companion pack).
- **Writing the skeptical review with enough force to be useful.** The AI's first draft was too polite. A skeptical review that does not make you flinch is not doing its job. I rewrote it to be genuinely adversarial.
- **Deciding what the harness should not do (and saying so explicitly in README).** The harness explicitly does not replace research taste, supervisor judgment, or empirical verification. This boundary is essential — without it, the harness becomes a crutch rather than a tool.

---

## With more time

- **Second worked example** from a live interpretability or control codebase, to show the harness works across different alignment sub-fields.
- **One actual notebook** running a mini-eval with the harness as context, so fellows see the bridge from skill output to executable code.
- **Tested prompt blocks** across Claude, GPT-4o, and Gemini to verify portability and flag model-specific behaviors.
- **Fellow-facing onboarding instructions** with common mistakes (e.g., treating the prompt block as a checklist rather than a scaffold, skipping the skeptical review step).
- **Stronger repro-triage examples** on real research repos, added back as an optional eighth skill for troubleshooting failed reproductions.
