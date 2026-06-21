# Validation status

## What this repo has been tested on
- Claude Code workflow for the included CoT faithfulness worked example
- End-to-end artifact flow:
  - abstract
  - research plan
  - cheapest test ladder
  - eval spec
  - ablation plan
  - skeptical review
  - weekly update

## What this repo has not been validated on
- direct portability to GPT-4o or Gemini interfaces
- live integration with a real reproduction codebase
- non-LLM domains
- fully automated chaining between skills

## Known limits
1. The skills are strongest for empirical LLM alignment work, not all AI safety research.
2. The worked example is illustrative. It demonstrates workflow quality, not experimental truth.
3. `skeptical-reviewer` requires human sharpening. AI outputs are usually too polite on the first pass.
4. `paper-to-plan` and `eval-design` can miss hidden infrastructure dependencies unless the user supplies them explicitly.
5. `writeup-scaffold` should not be used until the result is genuinely decision-ready.

## Human judgment remains essential for
- choosing the right research question
- deciding whether a result matters enough to pursue
- interpreting a proxy metric in context
- knowing when a plan is elegant but low-value
- deciding when to kill a project instead of scaling it

## Intended use
Treat this repo as a structured accelerator for good research habits.
Do not treat it as a substitute for research taste.
