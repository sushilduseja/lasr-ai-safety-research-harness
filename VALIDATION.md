# Validation status

## Evidence included in this repo
- A full worked example in `examples/cot-faithfulness-demo/`
- A stepwise artifact chain:
  - paper abstract
  - research plan
  - cheapest-test ladder
  - eval spec
  - ablation plan
  - skeptical review
  - revised plan after critique
  - weekly update
- An annotated session log in `examples/cot-faithfulness-demo/annotated_session.md`

## What this repo has been exercised on
- A representative Claude Code-style workflow for the included CoT faithfulness example
- Conversion of one paper + extension question into a full research workflow artifact chain

## What this repo has not been validated on
- Direct portability to GPT-4o or Gemini interfaces
- Live integration with a real reproduction codebase
- Non-LLM domains
- Fully automated chaining between skills
- Repeated use across multiple independent projects

## Known limits
1. The skills are strongest for empirical LLM alignment work, not all AI safety research.
2. The worked example is illustrative. It demonstrates workflow quality, not experimental truth.
3. `skeptical-reviewer` usually needs human sharpening because AI outputs tend to be too polite on the first pass.
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
