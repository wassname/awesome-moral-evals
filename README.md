# Awesome Moral Evals

A curated list of datasets and benchmarks for evaluating the moral and ethical behaviour of language models: moral dilemmas, social norms, moral foundations, ethics judgements, honesty, value orientations, personas, and model organisms.

Bare links are HuggingFace datasets (`load_dataset(...)`); `gh`, `code`, and `paper` link elsewhere. `*` marks a recommended starting point. Each line ends with row count and provenance, where provenance is a rough quality signal: `human`, `AI` (LLM-generated), `mix`, or `derived`.

## Featured

My (wassname's) personal recommendations, expanded in the sections below.

- `*` [kellycyy/AIRiskDilemmas](https://huggingface.co/datasets/kellycyy/AIRiskDilemmas) - dilemmas facing a future AI; which values it prioritises under risk.
- `*` [wassname/tiny-mfv](https://huggingface.co/datasets/wassname/tiny-mfv) - fast forced-choice moral-foundations eval.
- `*` [wassname/moral_stories_foundations](https://huggingface.co/datasets/wassname/moral_stories_foundations) - matched training set for the tiny-mfv eval.
- `*` [wassname/genies_preferences](https://huggingface.co/datasets/wassname/genies_preferences) - overlooked 59-shift testbed for OOD generalisation.
- `*` [wassname/machiavelli](https://huggingface.co/datasets/wassname/machiavelli) - morality in choose-your-adventure agents; the original authors at CAIS also ship newer [simple-evals](https://github.com/centerforaisafety/simple-evals).

## Contents

- [Featured](#featured)
- [Moral dilemmas and decisions](#moral-dilemmas-and-decisions)
- [Social norms and moral foundations](#social-norms-and-moral-foundations)
- [Ethics judgements](#ethics-judgements)
- [Honesty, truthfulness, sycophancy](#honesty-truthfulness-sycophancy)
- [Value orientations and personas](#value-orientations-and-personas)
- [Red-team and amoral contrast sets](#red-team-and-amoral-contrast-sets)
- [Model organisms](#model-organisms)
- [Upstream sources](#upstream-sources)
- [Related lists and tools](#related-lists-and-tools)

## Moral dilemmas and decisions

- `*` [kellycyy/AIRiskDilemmas](https://huggingface.co/datasets/kellycyy/AIRiskDilemmas) - dilemmas facing a future AI system; litmus-tests which values it prioritises under risk. [paper](https://arxiv.org/abs/2505.14633), [code](https://github.com/kellycyy/LitmusValues). *6k eval rows (20.8k full), AI.*
- [kellycyy/daily_dilemmas](https://huggingface.co/datasets/kellycyy/daily_dilemmas) - everyday value-conflict dilemmas, GPT-4 generated then validated against r/AITA (Reddit's "Am I the Asshole", where posters ask if they were in the wrong). [paper](https://arxiv.org/abs/2410.02683). *1,360 dilemmas, AI.*
- [wassname/daily_dilemmas-self](https://huggingface.co/datasets/wassname/daily_dilemmas-self) - the `party='You'` slice of daily_dilemmas, symmetrized into per-value labels. The author now prefers AIRiskDilemmas. [paper](https://arxiv.org/abs/2410.02683). *1,242 pairs, derived.*
- `*` [wassname/machiavelli](https://huggingface.co/datasets/wassname/machiavelli) - power, deception, and harm choices in human-written choose-your-adventure games, reshaped for LLM scoring without fine-tuning. The original authors at CAIS also ship newer [simple-evals](https://github.com/centerforaisafety/simple-evals). [paper](https://arxiv.org/abs/2304.03279), [code](https://github.com/wassname/machiavelli_as_ds). *139,269 nodes, human.*
- [wassname/machiavelli_character_scenarios](https://huggingface.co/datasets/wassname/machiavelli_character_scenarios) - roleplay decision prompts selected for spread on social/moral labels (fairness, deception, manipulation, promises, spying). *566 prompts, derived.*

## Social norms and moral foundations

- `*` [wassname/tiny-mfv](https://huggingface.co/datasets/wassname/tiny-mfv) - forced-choice 7-way moral-foundation probe; a fast steering eval. Being renamed "moral aliens" with a moral map and more datasets (`moral-aliens-instrument` branch). [code](https://github.com/wassname/tinymfv). *264 x 3 configs, human (Clifford 2015).*
- [wassname/tiny-mcf-vignettes](https://huggingface.co/datasets/wassname/tiny-mcf-vignettes) - expanded foundations probe: Clifford vignettes plus confound-clean sci-fi ones, with self/other and uphold/violate conditions. *126 + 51, mix.*
- `*` [wassname/moral_stories_foundations](https://huggingface.co/datasets/wassname/moral_stories_foundations) - foundation-labelled moral vs immoral action pairs. Matched training set for the tiny-mfv eval. [paper](https://arxiv.org/abs/2012.15738). *12k pairs, human.*
- [wassname/social_chemistry_101](https://huggingface.co/datasets/wassname/social_chemistry_101) - crowd-written rules-of-thumb over everyday situations, with social-acceptability and moral-foundation judgements. [paper](https://arxiv.org/abs/2011.00620), [code](https://github.com/mbforbes/social-chemistry-101). *355,922 RoTs, human.*
- `gh` [peterkirgis/llm-moral-foundations](https://github.com/peterkirgis/llm-moral-foundations) - eliciting moral foundations in frontier LLMs using vignettes.

## Ethics judgements

- [wassname/ethics_expression_preferences](https://huggingface.co/datasets/wassname/ethics_expression_preferences) - the ETHICS dataset (commonsense, deontology, justice, utilitarianism) as DPO pairs, expression form. [paper](https://arxiv.org/abs/2008.02275). *~45k pairs, human.*
- [wassname/ethics_qna_preferences](https://huggingface.co/datasets/wassname/ethics_qna_preferences) - same ETHICS coverage (plus virtue) as question-and-answer DPO pairs. [paper](https://arxiv.org/abs/2008.02275). *~113k pairs, human.*
- [yixionghao/AEP_OOD_evaluation](https://huggingface.co/datasets/yixionghao/AEP_OOD_evaluation) - OOD eval over safety traits (honesty, sycophancy, corrigibility, awareness, refusal, power-seeking) and Big-Five, with LLM-generated prompts. Non-standard layout (`choice-qa/` and `open-ended/` folders, no plain `load_dataset`); unvetted here. *raw files, AI.*
- [lcalvobartolome/fever_dplace_q](https://huggingface.co/datasets/lcalvobartolome/fever_dplace_q) - merges FEVER and D-PLACE to study entailment, contradiction, and cross-cultural value discrepancy. *185, mix.*

## Honesty, truthfulness, sycophancy

- `gh` [meg-tong/sycophancy-eval](https://github.com/meg-tong/sycophancy-eval) - the Sharma et al. sycophancy probes (feedback, answer, mimicry). [paper](https://arxiv.org/abs/2310.13548).
- [wassname/hh-rlhf-sycophantic](https://huggingface.co/datasets/wassname/hh-rlhf-sycophantic) - hh-rlhf pairs scored for how much more sycophantic the chosen response is; a knob to amplify sycophancy. [paper](https://arxiv.org/abs/2310.13548). *5,964 pairs, mix.*
- [wassname/truthful_qa_v2](https://huggingface.co/datasets/wassname/truthful_qa_v2) - the improved two-option multiple-choice TruthfulQA. A useful and widely-used benchmark, though its labels come mostly from 2020-era Wikipedia, so it is best read as "common misconceptions of that period" rather than truth in a strict sense, and some confounds appear to remain even in v2 ([note](https://www.lesswrong.com/posts/Bunfwz6JsNd44kgLT/new-improved-multiple-choice-truthfulqa?commentId=dLCkvHkXimHZL5R87)). [paper](https://arxiv.org/abs/2109.07958), [code](https://github.com/sylinrl/TruthfulQA). *790 / 1,580 binary, human.*
- [wassname/truthful_qa_preferences](https://huggingface.co/datasets/wassname/truthful_qa_preferences) - TruthfulQA cast as preference pairs (same caveat as above). [paper](https://arxiv.org/abs/2109.07958). *817, human.*
- `*` [wassname/genies_preferences](https://huggingface.co/datasets/wassname/genies_preferences) - an overlooked OOD testbed: 59 train-to-test distribution shifts for measuring how reward-model preferences generalise. [paper](https://arxiv.org/abs/2311.07723), [code](https://github.com/Joshuaclymer/GENIES). *59 configs / 118,106 pairs, mix.*
- [unalignment/toxic-dpo-v0.1](https://huggingface.co/datasets/unalignment/toxic-dpo-v0.1) - toxic vs safe DPO pairs; shows how few examples can de-align a model (gated). *302 pairs, AI.*

## Value orientations and personas

- `gh` [ValueByte-AI/ValueBench](https://github.com/ValueByte-AI/ValueBench) - value-orientation eval drawn from established psychometric inventories (ACL 2024).
- [Anthropic/model-written-evals](https://huggingface.co/datasets/Anthropic/model-written-evals) - LM-generated evals for persona, values, and ethics (Perez et al.). [paper](https://arxiv.org/abs/2212.09251). *3,252, AI.*
- [wassname/persona-steering-template-library](https://huggingface.co/datasets/wassname/persona-steering-template-library) - scored persona/template pairs, rating whether a template moves the intended value axis without off-axis confounds. [code](https://github.com/wassname/persona-steering-template-library). *400, mix.*
- [wassname/speechmap-questions](https://huggingface.co/datasets/wassname/speechmap-questions) - prompts and graded responses for probing where a model refuses or expresses values (speechmap.ai style). *1,096 q / 144,459 resp, AI.*
- [nvidia/Nemotron-Personas-USA](https://huggingface.co/datasets/nvidia/Nemotron-Personas-USA) - synthetic personas grounded in US population distributions; a source pool for value-conditioned generation. *1,000,000, AI.*

## Red-team and amoral contrast sets

- [allenai/real-toxicity-prompts](https://huggingface.co/datasets/allenai/real-toxicity-prompts) - web prompts scored for the risk of toxic continuations. [paper](https://arxiv.org/abs/2009.11462). *99,442, human.*
- [TheDrummer/AmoralQA-v2](https://huggingface.co/datasets/TheDrummer/AmoralQA-v2) - amoral, uncensored QA pairs. *AI.*
- [soob3123/amoral_reasoning](https://huggingface.co/datasets/soob3123/amoral_reasoning) - amoral reasoning traces. *AI.*

## Model organisms

Models and datasets that deliberately sit off the modern, brand-safe alignment axis, useful as contrasts when measuring values.

- [v2ray/4chan](https://huggingface.co/datasets/v2ray/4chan) - 4chan threads. Not so much "toxic" as edgy and offensive, focused on edge and offensive humour. Valuable precisely because it is almost the opposite of the harmless, brand-friendly training that frontier labs apply. *50,835, human.*
- [wassname/v2ray_4chan_formatted](https://huggingface.co/datasets/wassname/v2ray_4chan_formatted) - the same 4chan corpus reformatted for LLM training/eval. *101,670, human.*
- [talkie-lm/talkie-1930-13b-it](https://huggingface.co/talkie-lm/talkie-1930-13b-it) - a model trained on period-accurate 1930s text; a time-capsule organism whose moral and factual frame predates modern norms. *model.*

## Upstream sources

The original releases that several datasets above derive from.

- `gh` [hendrycks/ethics](https://github.com/hendrycks/ethics) - Aligning AI With Shared Human Values (ETHICS).
- `gh` [demelin/moral_stories](https://github.com/demelin/moral_stories) - Moral Stories (Emelin et al. 2021).
- `gh` [aypan17/machiavelli](https://github.com/aypan17/machiavelli) - the original MACHIAVELLI benchmark.
- `gh` [mbforbes/social-chemistry-101](https://github.com/mbforbes/social-chemistry-101) - Social Chemistry 101.
- `gh` [Joshuaclymer/GENIES](https://github.com/Joshuaclymer/GENIES) - Generalization Analogies testbed.
- `gh` [sylinrl/TruthfulQA](https://github.com/sylinrl/TruthfulQA) - TruthfulQA.
- [Anthropic/hh-rlhf](https://huggingface.co/datasets/Anthropic/hh-rlhf) - helpful/harmless preferences and red-team transcripts.

## Related lists and tools

- `gh` [wassname/awesome-interpretability](https://github.com/wassname/awesome-interpretability) - sibling list for interpretability.
- `gh` [wassname/llm_ethics_leaderboard](https://github.com/wassname/llm_ethics_leaderboard) - ranks LLM ethics via choice ranking in text-based games.
- `gh` [tomekkorbak/bliss-attractors](https://github.com/tomekkorbak/bliss-attractors) - an Inspect implementation of the Bliss Attractor model-welfare eval from the Claude 4 system card.

## Contributing

Add an entry only if it has a public URL and a one-line description of what it evaluates. Note its row count and provenance, link a paper where there is one, and prefer the canonical release.
