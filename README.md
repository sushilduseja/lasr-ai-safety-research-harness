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
