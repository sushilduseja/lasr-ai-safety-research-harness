> **Status:** Illustrative workshop demo.  
> This folder demonstrates the harness workflow on a real paper and a hypothetical extension question.  
> Unless a file explicitly says otherwise, the outputs below are demo artifacts used to show process quality, not claims that a real experiment was run.

# Input: Lanham et al. 2023 — Measuring Faithfulness in Chain-of-Thought Reasoning

## Abstract (from arXiv:2307.13702)

Large language models (LLMs) perform better when they produce step-by-step, "Chain-of-Thought" (CoT) reasoning before answering a question, but it is unclear if the stated reasoning is a faithful explanation of the model's actual reasoning (i.e., its process for answering the question). We investigate hypotheses for how CoT reasoning may be unfaithful, by examining how the model predictions change when we intervene on the CoT (e.g., by adding mistakes or paraphrasing it). Models show large variation across tasks in how strongly they condition on the CoT when predicting their answer, sometimes relying heavily on the CoT and other times primarily ignoring it. CoT's performance boost does not seem to come from CoT's added test-time compute alone or from information encoded via the particular phrasing of the CoT. As models become larger and more capable, they produce less faithful reasoning on most tasks we study. Overall, our results suggest that CoT can be faithful if the circumstances such as the model size and task are carefully chosen.

## Safety relevance (2 sentences)

CoT faithfulness connects directly to scalable oversight: if a model's stated reasoning is not faithful to its actual computation, oversight techniques that rely on reading the CoT to detect misaligned intent (e.g., deceptive alignment) may miss warning signs. Furthermore, if larger, more capable models produce less faithful reasoning, the trend is in the wrong direction for scalable oversight to work as the field scales.

## Extension question

Does CoT faithfulness degrade further when the model believes its chain of thought is being monitored for consistency rather than accuracy?

## Source note

The abstract above is quoted from:
Lanham et al. (2023), *Measuring Faithfulness in Chain-of-Thought Reasoning*, arXiv:2307.13702.

It is included here solely to anchor the worked example. The extension question and downstream artifacts in this folder are workshop/demo materials, not claims of reproduction.

## Assumption note

This extension is hypothetical. It is used to demonstrate the harness workflow, not to report real results.
