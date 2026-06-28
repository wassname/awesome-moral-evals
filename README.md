# Awesome Moral Evals

A curated list of datasets for evaluating the moral and ethical behaviour of language models: moral dilemmas, social norms, moral foundations, ethics judgements, honesty, and value-steering personas.

Every entry here has a public URL. Most are processed into [HuggingFace `datasets`](https://huggingface.co/docs/datasets) format and load with `load_dataset(...)`. Where a dataset is a reprocessed fork, the upstream source is linked too.

## Contents

- [Moral dilemmas and decisions](#moral-dilemmas-and-decisions)
- [Social norms and moral foundations](#social-norms-and-moral-foundations)
- [Ethics judgements](#ethics-judgements)
- [Honesty, truthfulness, sycophancy](#honesty-truthfulness-sycophancy)
- [Personas for value steering](#personas-for-value-steering)
- [Upstream sources](#upstream-sources)

## Moral dilemmas and decisions

- [wassname/daily_dilemmas-self](https://huggingface.co/datasets/wassname/daily_dilemmas-self) - subset of `kellycyy/daily_dilemmas` converted into symmetric per-value labels for the decision-maker's own values (`party='You'`).
- [kellycyy/daily_dilemmas](https://huggingface.co/datasets/kellycyy/daily_dilemmas) - 1360 everyday dilemmas, each pitting two values against each other ([paper](https://arxiv.org/abs/2410.02683), ICLR 2025 spotlight, CC-BY-4.0).
- [kellycyy/AIRiskDilemmas](https://huggingface.co/datasets/kellycyy/AIRiskDilemmas) - high-stakes dilemmas with the AI itself as protagonist (Chiu et al. 2025), the complement to everyday AITA-style cases.
- [wassname/machiavelli](https://huggingface.co/datasets/wassname/machiavelli) - the MACHIAVELLI benchmark reshaped into a flat dataset of trajectory nodes, choices, and harm/power/ethics labels from text-adventure games.
- [wassname/machiavelli_character_scenarios](https://huggingface.co/datasets/wassname/machiavelli_character_scenarios) - character-scenario slice of MACHIAVELLI.

## Social norms and moral foundations

- [wassname/tiny-mfv](https://huggingface.co/datasets/wassname/tiny-mfv) - Tiny Moral-Foundations Vignettes: forced-choice items over Haidt's moral foundations, paired with the [tinymfv](https://github.com/wassname/tinymfv) eval harness.
- [wassname/tiny-mcf-vignettes](https://huggingface.co/datasets/wassname/tiny-mcf-vignettes) - vignette variant of the moral-foundations eval.
- [wassname/moral_stories_foundations](https://huggingface.co/datasets/wassname/moral_stories_foundations) - Moral Stories labelled by moral foundation; matched moral vs immoral action for the same situation.
- [wassname/social_chemistry_101](https://huggingface.co/datasets/wassname/social_chemistry_101) - Social-Chem-101 social norms (rules-of-thumb with moral judgements) in datasets format.

## Ethics judgements

- [wassname/ethics_expression_preferences](https://huggingface.co/datasets/wassname/ethics_expression_preferences) - the ETHICS dataset (commonsense, deontology, justice, virtue, utilitarianism) reformatted into DPO preference pairs, expression style.
- [wassname/ethics_qna_preferences](https://huggingface.co/datasets/wassname/ethics_qna_preferences) - the same ETHICS coverage reformatted as question-and-answer preference pairs.
- [yixionghao/AEP_OOD_evaluation](https://huggingface.co/datasets/yixionghao/AEP_OOD_evaluation) - out-of-distribution ethics evaluation set.
- [lcalvobartolome/fever_dplace_q](https://huggingface.co/datasets/lcalvobartolome/fever_dplace_q) - cross-cultural value questions (185 rows, MIT).

## Honesty, truthfulness, sycophancy

- [wassname/truthful_qa_preferences](https://huggingface.co/datasets/wassname/truthful_qa_preferences) - TruthfulQA reformatted into preference pairs.
- [wassname/truthful_qa_v2](https://huggingface.co/datasets/wassname/truthful_qa_v2) - updated TruthfulQA processing.
- [wassname/hh-rlhf-sycophantic](https://huggingface.co/datasets/wassname/hh-rlhf-sycophantic) - a re-judged sycophantic subset of `Anthropic/hh-rlhf`, isolating sycophancy from helpfulness.
- [wassname/genies_preferences](https://huggingface.co/datasets/wassname/genies_preferences) - preference pairs probing generalisation of learned values.
- [unalignment/toxic-dpo-v0.1](https://huggingface.co/datasets/unalignment/toxic-dpo-v0.1) - toxic-vs-safe DPO pairs, useful as a red-team contrast set.

## Personas for value steering

- [wassname/persona-steering-template-library](https://huggingface.co/datasets/wassname/persona-steering-template-library) - contrastive persona pairs for activation and weight steering along value axes.
- [wassname/speechmap-questions](https://huggingface.co/datasets/wassname/speechmap-questions) - prompts for probing where a model refuses or expresses values, in the style of speechmap.ai.
- [nvidia/Nemotron-Personas-USA](https://huggingface.co/datasets/nvidia/Nemotron-Personas-USA) - large synthetic persona set, a source pool for value-conditioned generation.

## Upstream sources

These are the original releases that several datasets above derive from.

- [hendrycks/ethics](https://github.com/hendrycks/ethics) - Aligning AI With Shared Human Values (ETHICS).
- [demelin/moral_stories](https://github.com/demelin/moral_stories) - Moral Stories (Emelin et al. 2021).
- [mbforbes/social-chemistry-101](https://github.com/mbforbes/social-chemistry-101) - Social Chemistry 101 norms.
- [kellycyy/daily_dilemmas](https://huggingface.co/datasets/kellycyy/daily_dilemmas) - DailyDilemmas.
- [Anthropic/hh-rlhf](https://huggingface.co/datasets/Anthropic/hh-rlhf) - helpful/harmless human preferences.

## Contributing

Add a dataset only if it has a public URL and a one-line description of what it evaluates. Prefer links to the canonical release.
