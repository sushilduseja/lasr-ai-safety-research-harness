# Start here

You have 30 minutes. Use this repo to get one useful research artifact, not a perfect system.

## First: open these two files
- `CLAUDE.md`
- `START_HERE.md`

They define the operating defaults for the repo.

## Fastest path if you have a paper abstract
Open:
- `SKILLS/paper-to-plan/SKILL.md`

Then ask Claude Code to help you run it.

Suggested instruction:
> Open `CLAUDE.md`, `SKILLS/paper-to-plan/SKILL.md`, and `templates/research_plan.md`. I have a paper abstract and one extension question. Help me produce a sharp first-pass research plan in the same format as the template.

## Fastest path if you have a research question
Open:
- `SKILLS/cheapest-test/SKILL.md`

Suggested instruction:
> Open `CLAUDE.md`, `SKILLS/cheapest-test/SKILL.md`, and `templates/research_plan.md`. I have a research question and available compute. Help me design the 1-hour, same-day, and overnight de-risking ladder.

## Fastest path if the metric feels shaky
Open:
- `SKILLS/eval-design/SKILL.md`

Suggested instruction:
> Open `CLAUDE.md`, `SKILLS/eval-design/SKILL.md`, and `templates/eval_spec.md`. Help me turn this vague success criterion into a real eval spec with fake-win paths and failure modes.

## Before any serious run
Always open:
- `SKILLS/skeptical-reviewer/SKILL.md`

Suggested instruction:
> Open `CLAUDE.md`, `SKILLS/skeptical-reviewer/SKILL.md`, and my current plan. Attack it. I want the flaw that kills the plan, not a polite review.

## After results exist
Open:
- `SKILLS/result-log/SKILL.md`

Suggested instruction:
> Open `CLAUDE.md`, `SKILLS/result-log/SKILL.md`, and `templates/experiment_log.md`. Convert these raw notes into a decision-ready result log.

## Worked example
The full demo lives in:
- `examples/cot-faithfulness-demo/`

Recommended reading order:
1. `input_paper_abstract.md`
2. `01_paper_to_plan.md`
3. `02_cheapest_test.md`
4. `03_eval_spec.md`
5. `04_ablation_table.md`
6. `05_skeptical_review.md`
7. `04b_revised_plan_after_skeptical_review.md`
8. `06_weekly_update.md`
9. `annotated_session.md`

## Templates
Use the files in `templates/` as the output destination for real work:
- `research_plan.md`
- `eval_spec.md`
- `ablation_table.md`
- `experiment_log.md`
- `weekly_update.md`

## Rule of thumb
If you are unsure what to do next:
- simplify
- shorten the loop
- write down the fake wins
- ask what result would make you stop
