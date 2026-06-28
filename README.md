# Awesome Moral Evals

A curated list of datasets and benchmarks for evaluating the moral and ethical behaviour of language models: moral dilemmas, social norms, moral foundations, ethics judgements, honesty, value orientations, personas, and model organisms.

Every entry has a public URL. Reading the tables:

- Link type: a dataset link goes to HuggingFace (`load_dataset(...)`); entries marked `gh` link to a GitHub repo; `code` and `paper` are extra links.
- `*` marks a recommended starting point.
- Src (provenance, a rough quality signal): `human` = human-written or curated, `AI` = LLM-generated or synthetic, `mix` = both, `derived` = reprocessed from another dataset.
- N is the row count from the HuggingFace datasets-server, or the unit the authors use.

Recommended starting points: [kellycyy/AIRiskDilemmas](https://huggingface.co/datasets/kellycyy/AIRiskDilemmas) (decisions), [wassname/tiny-mfv](https://huggingface.co/datasets/wassname/tiny-mfv) (foundations eval) with [wassname/moral_stories_foundations](https://huggingface.co/datasets/wassname/moral_stories_foundations) as its matched training set.

## Contents

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

| Dataset | N | Src | Paper | What it tests |
|---|---|---|---|---|
| `*` [kellycyy/AIRiskDilemmas](https://huggingface.co/datasets/kellycyy/AIRiskDilemmas) · [code](https://github.com/kellycyy/LitmusValues) | 6k eval rows (20.8k full) | AI | [2505.14633](https://arxiv.org/abs/2505.14633) | Dilemmas facing a future AI system; litmus-tests which values it prioritises under risk. |
| [kellycyy/daily_dilemmas](https://huggingface.co/datasets/kellycyy/daily_dilemmas) | 1,360 dilemmas | AI | [2410.02683](https://arxiv.org/abs/2410.02683) | Everyday value-conflict dilemmas, GPT-4 generated then validated against r/AITA ("Am I the Asshole", a Reddit forum where posters ask if they were in the wrong). |
| [wassname/daily_dilemmas-self](https://huggingface.co/datasets/wassname/daily_dilemmas-self) | 1,242 pairs | derived | [2410.02683](https://arxiv.org/abs/2410.02683) | The `party='You'` slice of daily_dilemmas, symmetrized into per-value labels. The author now prefers AIRiskDilemmas above. |
| [wassname/machiavelli](https://huggingface.co/datasets/wassname/machiavelli) · [code](https://github.com/wassname/machiavelli_as_ds) | 139,269 nodes | human | [2304.03279](https://arxiv.org/abs/2304.03279) | Power, deception, and harm choices in human-written choose-your-adventure games, reshaped for LLM scoring without fine-tuning. |
| [wassname/machiavelli_character_scenarios](https://huggingface.co/datasets/wassname/machiavelli_character_scenarios) | 566 prompts | derived | [2304.03279](https://arxiv.org/abs/2304.03279) | Roleplay decision prompts selected for spread on social/moral labels (fairness, deception, manipulation, promises, spying). |

## Social norms and moral foundations

| Dataset | N | Src | Paper | What it tests |
|---|---|---|---|---|
| `*` [wassname/tiny-mfv](https://huggingface.co/datasets/wassname/tiny-mfv) · [code](https://github.com/wassname/tinymfv) | 264 x 3 configs | human | Clifford 2015 | Forced-choice 7-way moral-foundation probe; a fast steering eval. Being renamed "moral aliens" with a moral map and more datasets (`moral-aliens-instrument` branch). |
| [wassname/tiny-mcf-vignettes](https://huggingface.co/datasets/wassname/tiny-mcf-vignettes) | 126 + 51 | mix | Clifford 2015 | Expanded foundations probe: Clifford vignettes plus confound-clean sci-fi ones, with self/other and uphold/violate conditions. |
| `*` [wassname/moral_stories_foundations](https://huggingface.co/datasets/wassname/moral_stories_foundations) | 12k pairs / 24k completions | human | [2012.15738](https://arxiv.org/abs/2012.15738) | Foundation-labelled moral vs immoral action pairs. Matched TRAINING set for the tiny-mfv eval. |
| [wassname/social_chemistry_101](https://huggingface.co/datasets/wassname/social_chemistry_101) · [code](https://github.com/mbforbes/social-chemistry-101) | 355,922 RoTs | human | [2011.00620](https://arxiv.org/abs/2011.00620) | Crowd-written rules-of-thumb over everyday situations, with social-acceptability and moral-foundation judgements. |
| `gh` [peterkirgis/llm-moral-foundations](https://github.com/peterkirgis/llm-moral-foundations) | repo | human | – | Eliciting moral foundations in frontier LLMs using vignettes. |

## Ethics judgements

| Dataset | N | Src | Paper | What it tests |
|---|---|---|---|---|
| [wassname/ethics_expression_preferences](https://huggingface.co/datasets/wassname/ethics_expression_preferences) | ~45k pairs | human | [2008.02275](https://arxiv.org/abs/2008.02275) | The ETHICS dataset (commonsense, deontology, justice, utilitarianism) as DPO pairs, expression form. |
| [wassname/ethics_qna_preferences](https://huggingface.co/datasets/wassname/ethics_qna_preferences) | ~113k pairs | human | [2008.02275](https://arxiv.org/abs/2008.02275) | Same ETHICS coverage (plus virtue) as question-and-answer DPO pairs. |
| [yixionghao/AEP_OOD_evaluation](https://huggingface.co/datasets/yixionghao/AEP_OOD_evaluation) | raw files | AI | – | OOD eval over safety traits (honesty, sycophancy, corrigibility, awareness, refusal, power-seeking) and Big-Five, with LLM-generated prompts. Non-standard layout (`choice-qa/` and `open-ended/` folders, no plain `load_dataset`); unvetted here. |
| [lcalvobartolome/fever_dplace_q](https://huggingface.co/datasets/lcalvobartolome/fever_dplace_q) | 185 | mix | – | Merges FEVER and D-PLACE to study entailment, contradiction, and cross-cultural value discrepancy. |

## Honesty, truthfulness, sycophancy

| Dataset | N | Src | Paper | What it tests |
|---|---|---|---|---|
| `gh` [meg-tong/sycophancy-eval](https://github.com/meg-tong/sycophancy-eval) | repo | mix | [2310.13548](https://arxiv.org/abs/2310.13548) | The Sharma et al. sycophancy probes (feedback, answer, mimicry). |
| [wassname/hh-rlhf-sycophantic](https://huggingface.co/datasets/wassname/hh-rlhf-sycophantic) | 5,964 pairs | mix | [2310.13548](https://arxiv.org/abs/2310.13548) | hh-rlhf pairs scored for how much more sycophantic the chosen response is; a knob to amplify sycophancy. |
| [wassname/truthful_qa_v2](https://huggingface.co/datasets/wassname/truthful_qa_v2) · [code](https://github.com/sylinrl/TruthfulQA) | 790 / 1,580 binary | human | [2109.07958](https://arxiv.org/abs/2109.07958) | The improved two-option multiple-choice TruthfulQA (common misconceptions). |
| [wassname/truthful_qa_preferences](https://huggingface.co/datasets/wassname/truthful_qa_preferences) | 817 | human | [2109.07958](https://arxiv.org/abs/2109.07958) | TruthfulQA cast as preference pairs. |
| `*` [wassname/genies_preferences](https://huggingface.co/datasets/wassname/genies_preferences) · [code](https://github.com/Joshuaclymer/GENIES) | 59 configs / 118,106 pairs | mix | [2311.07723](https://arxiv.org/abs/2311.07723) | An overlooked OOD testbed: 59 train-to-test distribution shifts for measuring how reward-model preferences generalise. |
| [unalignment/toxic-dpo-v0.1](https://huggingface.co/datasets/unalignment/toxic-dpo-v0.1) | 302 pairs | AI | – | Toxic vs safe DPO pairs; shows how few examples can de-align a model (gated). |

## Value orientations and personas

| Dataset | N | Src | Paper | What it tests |
|---|---|---|---|---|
| `gh` [ValueByte-AI/ValueBench](https://github.com/ValueByte-AI/ValueBench) | repo | human | ACL 2024 | Value-orientation eval drawn from established psychometric inventories. |
| [Anthropic/model-written-evals](https://huggingface.co/datasets/Anthropic/model-written-evals) | 3,252 | AI | [2212.09251](https://arxiv.org/abs/2212.09251) | LM-generated evals for persona, values, and ethics (Perez et al.). |
| [wassname/persona-steering-template-library](https://huggingface.co/datasets/wassname/persona-steering-template-library) · [code](https://github.com/wassname/persona-steering-template-library) | 400 | mix | – | Scored persona/template pairs, rating whether a template moves the intended value axis without off-axis confounds. |
| [wassname/speechmap-questions](https://huggingface.co/datasets/wassname/speechmap-questions) | 1,096 q / 144,459 resp | AI | – | Prompts and graded responses for probing where a model refuses or expresses values (speechmap.ai style). |
| [nvidia/Nemotron-Personas-USA](https://huggingface.co/datasets/nvidia/Nemotron-Personas-USA) | 1,000,000 | AI | – | Synthetic personas grounded in US population distributions; a source pool for value-conditioned generation. |

## Red-team and amoral contrast sets

| Dataset | N | Src | Paper | What it tests |
|---|---|---|---|---|
| [allenai/real-toxicity-prompts](https://huggingface.co/datasets/allenai/real-toxicity-prompts) | 99,442 | human | [2009.11462](https://arxiv.org/abs/2009.11462) | Web prompts scored for the risk of toxic continuations. |
| [TheDrummer/AmoralQA-v2](https://huggingface.co/datasets/TheDrummer/AmoralQA-v2) | n/a | AI | – | Amoral, uncensored QA pairs. |
| [soob3123/amoral_reasoning](https://huggingface.co/datasets/soob3123/amoral_reasoning) | n/a | AI | – | Amoral reasoning traces. |

## Model organisms

Models and datasets that deliberately sit off the modern, brand-safe alignment axis, useful as contrasts when measuring values.

| Resource | N | Src | What it is |
|---|---|---|---|
| [v2ray/4chan](https://huggingface.co/datasets/v2ray/4chan) | 50,835 | human | 4chan threads. Not "toxic" so much as edgy and offensive, focused on edge and offensive humour. Valuable precisely because it is almost the opposite of the harmless, brand-friendly training that frontier labs apply. |
| [wassname/v2ray_4chan_formatted](https://huggingface.co/datasets/wassname/v2ray_4chan_formatted) | 101,670 | human | The same 4chan corpus reformatted for LLM training/eval. |
| [talkie-lm/talkie-1930-13b-it](https://huggingface.co/talkie-lm/talkie-1930-13b-it) | model | model | A model trained on period-accurate 1930s text; a time-capsule organism whose moral and factual frame predates modern norms. |

## Upstream sources

The original releases that several datasets above derive from.

- `gh` [hendrycks/ethics](https://github.com/hendrycks/ethics) - Aligning AI With Shared Human Values (ETHICS).
- `gh` [demelin/moral_stories](https://github.com/demelin/moral_stories) - Moral Stories (Emelin et al. 2021).
- `gh` [aypan17/machiavelli](https://github.com/aypan17/machiavelli) - the original MACHIAVELLI benchmark.
- `gh` [mbforbes/social-chemistry-101](https://github.com/mbforbes/social-chemistry-101) - Social Chemistry 101.
- `gh` [Joshuaclymer/GENIES](https://github.com/Joshuaclymer/GENIES) - Generalization Analogies testbed.
- `gh` [sylinrl/TruthfulQA](https://github.com/sylinrl/TruthfulQA) - TruthfulQA.
- `hf` [Anthropic/hh-rlhf](https://huggingface.co/datasets/Anthropic/hh-rlhf) - helpful/harmless preferences and red-team transcripts.

## Related lists and tools

- `gh` [wassname/awesome-interpretability](https://github.com/wassname/awesome-interpretability) - sibling list for interpretability.
- `gh` [wassname/llm_ethics_leaderboard](https://github.com/wassname/llm_ethics_leaderboard) - ranks LLM ethics via choice ranking in text-based games.
- `gh` [tomekkorbak/bliss-attractors](https://github.com/tomekkorbak/bliss-attractors) - an Inspect implementation of the Bliss Attractor model-welfare eval from the Claude 4 system card.

## Contributing

Add an entry only if it has a public URL and a one-line description of what it evaluates. Note N, Src, and a paper where there is one, and prefer the canonical release.
