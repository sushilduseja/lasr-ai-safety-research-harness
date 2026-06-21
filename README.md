# AI Safety Research Harness

A Claude Code-native skill pack for technical AI safety researchers.

## What it is
This repo packages seven reusable research skills for empirical AI safety work:
- paper-to-plan
- cheapest-test
- eval-design
- ablation-planner
- skeptical-reviewer
- result-log
- writeup-scaffold

Each skill is a single `SKILL.md` file with:
- a fixed structure
- opinionated defaults
- AI safety-specific cautions
- a copy-pastable prompt block

## What problem it solves
Fluent AI use is not systematic AI use.

Strong researchers already use Claude Code, summarize papers with AI, and mix hand-written and AI-assisted code during research work. The main gap is usually not basic prompting ability. It is the absence of repeatable defaults for:
- scoping tractable extensions
- choosing the cheapest informative test
- designing evals that resist fake wins
- deciding ablations before running
- stress-testing plans adversarially
- logging results cleanly enough for immediate action

This repo turns ad hoc AI help into a repeatable research workflow.

## Designed for
Researchers working on empirical AI safety problems such as:
- evals
- scalable oversight
- chain-of-thought faithfulness
- model organisms
- control
- adversarial robustness

## Quickstart in Claude Code
1. Open this repo in Claude Code.
2. Open `CLAUDE.md` and `START_HERE.md`.
3. Pick the skill that matches your current bottleneck.
4. Copy the prompt block from that `SKILL.md`.
5. Run it on your project inputs.
6. Save the output using the matching template in `templates/`.
7. Before committing to a plan, run `skeptical-reviewer`.

## Fastest paths
- Have a paper abstract + extension question? → `SKILLS/paper-to-plan/SKILL.md`
- Have a research question + need the first experiment? → `SKILLS/cheapest-test/SKILL.md`
- Have a metric but don't trust it? → `SKILLS/eval-design/SKILL.md`
- Have a plan and want to break it? → `SKILLS/skeptical-reviewer/SKILL.md`
- Have results and need a sharp update? → `SKILLS/result-log/SKILL.md`

## Worked example
See `examples/cot-faithfulness-demo/` for a full end-to-end demo using:

Lanham et al. 2023, *Measuring Faithfulness in Chain-of-Thought Reasoning*  
Extension question: whether explicit monitoring framing further degrades CoT faithfulness.

The demo is a **worked example for workshop purposes**, not a claim that a real experiment was run.
The screenshot assets used in the final submission are documented in `screenshots/README.md`.

Reference paper: Lanham et al. (2023), *Measuring Faithfulness in Chain-of-Thought Reasoning*, arXiv:2307.13702. This worked example uses the paper as a cited workshop anchor and does not claim exact reproduction.

## Why this is AI safety-specific
The skills encode defaults that matter disproportionately in alignment work:
- fastest informative test before expensive infra
- explicit fake-win paths in every eval
- pivot/kill criteria written before running
- skepticism about output-level proxies
- null results treated as useful evidence
- controlled scope rather than impressive sprawl

## What this repo is not
This is not:
- a general productivity pack
- a literature summarizer
- an official reproduction package for any paper
- a substitute for supervisor judgment

This repo improves execution discipline and research process quality.
It does not replace research taste.

## Validation status
Designed for Claude Code.
See `VALIDATION.md` for tested scope, known limits, and where human judgment remains essential.

"This harness does not replace research judgment. It makes good judgment easier to execute consistently."
