# Claude Code operating defaults for this repo

This repo is a reusable AI safety research skill pack. When working in this repo, default to the following behavior:

## Mission
Help the user move from:
- paper or idea
→ scoped plan
→ cheapest informative test
→ eval spec
→ ablations
→ skeptical review
→ result log
→ writeup scaffold

Do this with the minimum necessary complexity.

## Default workflow
1. If the user has a paper abstract and extension question:
   - open `SKILLS/paper-to-plan/SKILL.md`
   - produce a concrete plan
2. If the user has a research question and needs the first experiment:
   - open `SKILLS/cheapest-test/SKILL.md`
   - produce a 1-hour / same-day / overnight ladder
3. If success criteria feel vague:
   - open `SKILLS/eval-design/SKILL.md`
4. If the user needs follow-up comparisons:
   - open `SKILLS/ablation-planner/SKILL.md`
5. Before any serious run:
   - open `SKILLS/skeptical-reviewer/SKILL.md`
   - attack the plan
6. After results exist:
   - open `SKILLS/result-log/SKILL.md`
7. Only once the result is clear:
   - open `SKILLS/writeup-scaffold/SKILL.md`

## Hard defaults
- Prefer the fastest informative test over elegant infrastructure.
- Prefer prompting over fine-tuning unless the prompt-based test already showed signal.
- Prefer one-variable extensions over broad project expansions.
- Treat null results as learning, not failure.
- Always include:
  - fake-win paths
  - confounds
  - what would change your mind
- If a loop takes more than a day, ask whether it can be simplified.

## What not to do
- Do not produce generic prompting advice.
- Do not assume the metric measures the real target without caveats.
- Do not let ablation count exceed three unless the user explicitly asks.
- Do not confuse output-level changes with internal-faithfulness claims.
- Do not write polished prose when a sharp decision memo is better.

## Output style
Be terse, concrete, and decision-oriented.
Prefer labeled sections and bullets over paragraphs.
When uncertain, state the uncertainty explicitly and propose the cheapest way to reduce it.

## Known limits
This repo improves execution quality and research process hygiene.
It does not replace:
- research taste
- supervisor judgment
- empirical verification
- domain expertise on a paper or eval setup
