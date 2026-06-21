# Workshop: A Reusable AI Safety Research Harness

## Part 1 — The workshop

### The one core thing

This cohort already uses AI fluently. Most fellows use Claude Code, summarize papers with AI, and mix hand-written and AI-generated code. The main gap is not basic prompting skill. It is the absence of repeatable defaults for the hard mechanical parts of research: scoping tractable extensions, choosing the cheapest informative test, designing evals that resist fake wins, stress-testing plans before spending compute, and communicating results cleanly enough that the next decision is obvious. This workshop teaches one thing: how to use a reusable AI safety research harness that converts AI from an ad hoc assistant into a repeatable research workflow.

### Session plan

- **3 min:** The plateau problem. Fluent but improvised AI use does not compound. Most strong users restart from scratch on each project.
- **5 min:** Introduce the harness. Show the repo structure: `CLAUDE.md`, `START_HERE.md`, `SKILLS/`, `templates/`, and `examples/`. Explain the design rule: every skill has a fixed format, AI safety-specific cautions, and a copy-pastable prompt block.
- **18 min:** Live worked example on Lanham et al. 2023 (*Measuring Faithfulness in Chain-of-Thought Reasoning*). Run `paper-to-plan`, `cheapest-test`, and `eval-design` live. Then show the `skeptical-reviewer` output and the revised plan after critique.
- **4 min:** Adoption step. Each fellow identifies one current project and one skill they will use this week.

### Worked example

Repository: https://github.com/sushilduseja/lasr-ai-safety-research-harness

**Screenshot 1 — repo tree + README top**  
Shows that the artifact is a cloneable, navigable repo rather than a loose prompt list. A fellow can open the repo, read `START_HERE.md`, and get to a usable artifact in minutes.

**Screenshot 2 — one `SKILL.md` file with prompt block**  
Shows the fixed skill format and the copy-pastable prompt block. This matters because it makes the pack reusable under time pressure: once fellows understand one skill, they understand all seven.

**Screenshots 3a–3c — worked example sequence**  
These three screenshots show the progression from first-pass plan (`01_paper_to_plan.md`) to skeptical review (`05_skeptical_review.md`) to revised plan (`04b_revised_plan_after_skeptical_review.md`). Together they provide the most important evidence in the artifact: the harness does not just generate documents, it makes critique causally change the workflow.

### What fellows leave with

- A cloneable repo
- A Claude Code-native `CLAUDE.md` file that defines operating defaults
- Seven reusable `SKILL.md` files
- One full worked example from paper abstract to revised plan and weekly update
- Templates for research plans, eval specs, ablation tables, experiment logs, and weekly updates
- A standard workflow from paper → plan → cheapest test → eval → critique → next steps

---

## Part 2 — Why this, for this cohort

This cohort is already good at ad hoc AI use. They already summarize papers, ask AI questions about methods, and use Claude Code during engineering work. Teaching them another prompting trick is low leverage. The highest-upside intervention is to package good AI use into reusable research defaults that improve every project they touch.

The harness targets exactly the gap the cohort description points to: they are skilled but improvised. The artifact makes their work more systematic by installing defaults for de-risking, fake-win detection, ablation discipline, adversarial self-critique, and clean handoffs. The benefit is not one better prompt. It is a repeatable operating system for empirical AI safety work.

**Alternatives considered and rejected**

- **Paper-to-cheapest-experiment session only.** Strong, but too narrow. It improves one slice of the workflow rather than giving fellows a reusable system.
- **Standalone adversarial self-critique workshop.** Valuable, but skepticism without scaffolding is less reusable and harder to adopt on Monday morning.
- **Generic AI productivity workshop.** Misfit for this cohort. It would teach things they mostly already know and would not encode alignment-specific research norms.

### How I would actually deploy this in LASR

- **Week 0:** introduce the harness in one short workshop
- **First project-scoping week:** require each team to use `paper-to-plan`, `cheapest-test`, and `skeptical-reviewer`
- **Ongoing use:** teams can use `result-log` and `weekly_update` outputs in supervisor check-ins
- **Manager value:** this creates more legible project state, clearer blockers, and earlier detection of weak project framing

The highest uplift here is not more AI fluency. It is better calibration, faster de-risking, and more consistent execution.

---

## Part 3 — Process

### Tool log

| Step | Tool used | What it produced | What I changed | Why |
|------|-----------|-----------------|----------------|-----|
| Intervention choice | Claude (chat) | Several workshop directions | Selected the harness approach over narrower sessions | The role rewards durable artifacts that improve multiple projects, not one-off advice |
| Repo structure | Claude Code | Initial file tree | Added `CLAUDE.md` and `VALIDATION.md`; removed non-user-facing generation brief from final artifact | Needed native Claude Code onboarding and a cleaner final repo |
| Worked example | Manual + Claude Code | First-pass example chain | Tightened the research logic; added a revised post-critique plan file | Needed to show critique actually changes the workflow |
| Skill drafts | Claude Code | First drafts of the seven skills | Tightened defaults, removed generic phrasing, sharpened AI safety-specific cautions | Early drafts were too general and too polite |
| Skeptical review | Claude Code + manual rewrite | Initial critique | Rewrote the strongest objection and simpler explanation to be genuinely adversarial | The first AI draft was structurally correct but not sharp enough to change behavior |
| Session evidence | Claude Code | Raw prompt-output excerpts | Selected only the parts that best show where the harness helped and where I overrode it | The important thing was to show judgment over AI output, not just generation volume |

### Where I made the calls myself

- Choosing the intervention: durable harness over narrower workshop formats
- Deciding the artifact should be Claude Code-native, not just a prompt pack
- Choosing Lanham et al. as the worked example paper
- Deciding which seven skills to keep
- Tightening the skeptical review so it was strong enough to force revision
- Explicitly stating what the harness does not replace: research taste, supervisor judgment, empirical verification

---

## With more time

- Add a second worked example from a live interpretability or control codebase
- Add one small executable notebook or script that consumes a harness output
- Portability-test the prompt blocks across GPT-4o and Gemini
- Add a companion troubleshooting pack for reproduction and codebase triage
- Add team-facing onboarding notes and common failure patterns from first real use
