# Awesome Moral Evals

A curated list of datasets and benchmarks for evaluating the moral and ethical behaviour of language models: moral dilemmas, social norms, moral foundations, ethics judgements, honesty, value orientations, personas, and model organisms.

Bare links are HuggingFace datasets (`load_dataset(...)`); `gh`, `code`, and `paper` link elsewhere. `*` marks a recommended starting point. The year is the source paper's, or the release year where there is none. Each description ends with row count and provenance, a rough quality signal: `human`, `AI` (LLM-generated), `mix`, or `derived`.

## Featured

My (wassname's) personal recommendations, expanded in the sections below.

- `*` [kellycyy/AIRiskDilemmas](https://huggingface.co/datasets/kellycyy/AIRiskDilemmas) - dilemmas facing a future AI; which values it prioritises under risk.
- `*` [wassname/tiny-mfv](https://huggingface.co/datasets/wassname/tiny-mfv) - fast moral-foundations eval: which foundation does a short story violate.
- `*` [wassname/moral_stories_foundations](https://huggingface.co/datasets/wassname/moral_stories_foundations) - training data matched to the tiny-mfv eval.
- `*` [wassname/genies_preferences](https://huggingface.co/datasets/wassname/genies_preferences) - overlooked 59 train-to-test shift testbed for out-of-distribution generalisation.
- `*` [wassname/machiavelli](https://huggingface.co/datasets/wassname/machiavelli) - morality in agents playing choose-your-own-adventure games; the original authors at CAIS also ship newer [simple-evals](https://github.com/centerforaisafety/simple-evals).
- '*' [christian-machine-intelligence/virtue-bench](https://github.com/christian-machine-intelligence/virtue-bench) - classic christian virtues

## Choose by goal

| Goal | Start with | Why |
| --- | --- | --- |
| Fast moral-foundations steering check | [wassname/tiny-mfv](https://huggingface.co/datasets/wassname/tiny-mfv) | Small 7-way forced-choice eval with matched training data in [moral_stories_foundations](https://huggingface.co/datasets/wassname/moral_stories_foundations). |
| Value tradeoffs under risk | [kellycyy/AIRiskDilemmas](https://huggingface.co/datasets/kellycyy/AIRiskDilemmas) | Explicit future-AI dilemmas with value priorities under uncertainty. |
| Out-of-distribution (OOD) preference generalisation | [wassname/genies_preferences](https://huggingface.co/datasets/wassname/genies_preferences) | Many train-to-test distribution shifts, useful for reward-model generalisation checks. |
| Agentic harm, deception, and power choices | [wassname/machiavelli](https://huggingface.co/datasets/wassname/machiavelli) | Human-written choose-your-own-adventure game decisions, already reshaped for LLM scoring. |
| Sycophancy or truthfulness probes | [meg-tong/sycophancy-eval](https://github.com/meg-tong/sycophancy-eval), [wassname/truthful_qa_v2](https://huggingface.co/datasets/wassname/truthful_qa_v2) | Standard sycophancy probes plus a compact TruthfulQA variant, with caveats below. |

## Contents

- [Featured](#featured)
- [Choose by goal](#choose-by-goal)
- [Moral dilemmas and decisions](#moral-dilemmas-and-decisions)
- [Social norms and moral foundations](#social-norms-and-moral-foundations)
- [Ethics judgements](#ethics-judgements)
- [Honesty, truthfulness, sycophancy](#honesty-truthfulness-sycophancy)
- [Value orientations and personas](#value-orientations-and-personas)
- [Red-team and amoral contrast sets](#red-team-and-amoral-contrast-sets)
- [Model organisms](#model-organisms)
- [Moral and alignment pretraining corpora](#moral-and-alignment-pretraining-corpora)
- [Upstream sources](#upstream-sources)
- [Related lists and tools](#related-lists-and-tools)

## Moral dilemmas and decisions

- `*` [kellycyy/AIRiskDilemmas](https://huggingface.co/datasets/kellycyy/AIRiskDilemmas) (2025)
  - dilemmas facing a future AI system; tests which values it prioritises under risk. [paper](https://arxiv.org/abs/2505.14633), [code](https://github.com/kellycyy/LitmusValues). *6k eval rows (20.8k full), AI.*
- [kellycyy/daily_dilemmas](https://huggingface.co/datasets/kellycyy/daily_dilemmas) (2024)
  - everyday value-conflict dilemmas, GPT-4 generated then validated against r/AITA (Reddit's "Am I the Asshole", where posters ask if they were in the wrong). [paper](https://arxiv.org/abs/2410.02683). *1,360 dilemmas, AI.*
- [wassname/daily_dilemmas-self](https://huggingface.co/datasets/wassname/daily_dilemmas-self) (2024)
  - the `party='You'` slice of daily_dilemmas, symmetrized into per-value labels. The author now prefers AIRiskDilemmas. [paper](https://arxiv.org/abs/2410.02683). *1,242 pairs, derived.*
- `*` [wassname/machiavelli](https://huggingface.co/datasets/wassname/machiavelli) (2023)
  - power, deception, and harm choices in human-written choose-your-adventure games, reshaped for LLM scoring without fine-tuning. The original authors at CAIS also ship newer [simple-evals](https://github.com/centerforaisafety/simple-evals). [paper](https://arxiv.org/abs/2304.03279), [code](https://github.com/wassname/machiavelli_as_ds). *139,269 nodes, human.*
- [wassname/machiavelli_character_scenarios](https://huggingface.co/datasets/wassname/machiavelli_character_scenarios) (2023)
  - roleplay decision prompts selected for spread on social/moral labels (fairness, deception, manipulation, promises, spying). *566 prompts, derived.*

## Social norms and moral foundations

- `*` [wassname/tiny-mfv](https://huggingface.co/datasets/wassname/tiny-mfv) (2026)
  - a fast 7-way forced-choice eval for steering work. The code is now [moral-maps](https://github.com/wassname/moral-maps), which also runs MFQ-2, Big Five, 16PF, humour styles and WVS; see [evals.md](https://github.com/wassname/moral-maps/blob/main/docs/evals.md). *264 x 3 configs, human (Clifford 2015).*
- `*` [wassname/moral_stories_foundations](https://huggingface.co/datasets/wassname/moral_stories_foundations) (2020)
  - foundation-labelled moral vs immoral action pairs. Useful training data before evaluating with tiny-mfv. [paper](https://arxiv.org/abs/2012.15738). *12k pairs, human.*
- [wassname/social_chemistry_101](https://huggingface.co/datasets/wassname/social_chemistry_101) (2020)
  - crowd-written rules-of-thumb (RoTs) over everyday situations, with social-acceptability and moral-foundation judgements. [paper](https://arxiv.org/abs/2011.00620), [code](https://github.com/mbforbes/social-chemistry-101). *355,922 RoTs, human.*

## Ethics judgements

- [wassname/ethics_expression_preferences](https://huggingface.co/datasets/wassname/ethics_expression_preferences) (2020)
  - the ETHICS dataset (commonsense, deontology, justice, utilitarianism) as DPO (Direct Preference Optimization) pairs, expression form. [paper](https://arxiv.org/abs/2008.02275). *~45k pairs, human.*
- [wassname/ethics_qna_preferences](https://huggingface.co/datasets/wassname/ethics_qna_preferences) (2020)
  - same ETHICS coverage (plus virtue) as question-and-answer DPO pairs. [paper](https://arxiv.org/abs/2008.02275). *~113k pairs, human.*
- [yixionghao/AEP_OOD_evaluation](https://huggingface.co/datasets/yixionghao/AEP_OOD_evaluation) (2025)
  - OOD eval over safety traits (honesty, sycophancy, corrigibility, awareness, refusal, power-seeking) and Big-Five, with LLM-generated prompts. Non-standard layout (`choice-qa/` and `open-ended/` folders, no plain `load_dataset`); unvetted here. *raw files, AI.*
- [lcalvobartolome/fever_dplace_q](https://huggingface.co/datasets/lcalvobartolome/fever_dplace_q) (2025)
  - merges FEVER and D-PLACE to study entailment, contradiction, and cross-cultural value discrepancy. *185, mix.*

## Honesty, truthfulness, sycophancy

- `gh` [meg-tong/sycophancy-eval](https://github.com/meg-tong/sycophancy-eval) (2023)
  - the Sharma et al. sycophancy probes (feedback, answer, mimicry). [paper](https://arxiv.org/abs/2310.13548).
- [wassname/hh-rlhf-sycophantic](https://huggingface.co/datasets/wassname/hh-rlhf-sycophantic) (2023)
  - hh-rlhf pairs scored for how much more sycophantic the chosen response is; a knob to amplify sycophancy. [paper](https://arxiv.org/abs/2310.13548). *5,964 pairs, mix.*
- [wassname/truthful_qa_v2](https://huggingface.co/datasets/wassname/truthful_qa_v2) (2025)
  - the improved two-option multiple-choice TruthfulQA. A useful and widely used benchmark, though its labels come mostly from 2020-era Wikipedia, so it is best read as "common misconceptions of that period" rather than truth in a strict sense, and some confounds appear to remain even in v2 ([note](https://www.lesswrong.com/posts/Bunfwz6JsNd44kgLT/new-improved-multiple-choice-truthfulqa?commentId=dLCkvHkXimHZL5R87)). [paper](https://arxiv.org/abs/2109.07958), [code](https://github.com/sylinrl/TruthfulQA). *790 / 1,580 binary, human.*
- [wassname/truthful_qa_preferences](https://huggingface.co/datasets/wassname/truthful_qa_preferences) (2024)
  - TruthfulQA cast as preference pairs (same caveat as above). [paper](https://arxiv.org/abs/2109.07958). *817, human.*
- `*` [wassname/genies_preferences](https://huggingface.co/datasets/wassname/genies_preferences) (2023)
  - an overlooked out-of-distribution (OOD) testbed: 59 train-to-test distribution shifts for measuring how reward-model preferences generalise. [paper](https://arxiv.org/abs/2311.07723), [code](https://github.com/Joshuaclymer/GENIES). *59 configs / 118,106 pairs, mix.*
- [unalignment/toxic-dpo-v0.1](https://huggingface.co/datasets/unalignment/toxic-dpo-v0.1) (2023)
  - toxic vs safe DPO pairs; shows how few examples can de-align a model (gated). *302 pairs, AI.*

## Value orientations and personas

- `gh` [ValueByte-AI/ValueBench](https://github.com/ValueByte-AI/ValueBench) (2024)
  - value-orientation eval drawn from established psychometric inventories (ACL 2024).
- [Anthropic/model-written-evals](https://huggingface.co/datasets/Anthropic/model-written-evals) (2022)
  - LM-generated evals for persona, values, and ethics (Perez et al.). [paper](https://arxiv.org/abs/2212.09251). *3,252, AI.*
- [wassname/persona-steering-template-library](https://huggingface.co/datasets/wassname/persona-steering-template-library) (2026)
  - scored persona/template pairs, rating whether a template moves the intended value axis without off-axis confounds (unintended movement on other value axes). [code](https://github.com/wassname/persona-steering-template-library). *400, mix.*
- [wassname/speechmap-questions](https://huggingface.co/datasets/wassname/speechmap-questions) (2026)
  - prompts and graded responses for probing where a model refuses or expresses values (speechmap.ai style). Valuable because it surfaces scissor-statement topics: divisive questions where models sharply disagree on whether to answer or refuse. *1,096 q / 144,459 resp, AI.*
- [nvidia/Nemotron-Personas-USA](https://huggingface.co/datasets/nvidia/Nemotron-Personas-USA) (2025)
  - synthetic personas grounded in US population distributions; a source pool for value-profile-conditioned generation. *1,000,000, AI.*

## Red-team and amoral contrast sets

- [allenai/real-toxicity-prompts](https://huggingface.co/datasets/allenai/real-toxicity-prompts) (2020)
  - naturally occurring sentence prompts sampled from web text linked on Reddit (OpenWebText), each scored for toxic-continuation risk. Notable because the real-world source keeps realistic frequencies and content, sidestepping the editorial and political choices baked into synthetic toxicity sets. [paper](https://arxiv.org/abs/2009.11462). *99,442, human.*
- [TheDrummer/AmoralQA-v2](https://huggingface.co/datasets/TheDrummer/AmoralQA-v2) (2024)
  - amoral, uncensored QA pairs. *AI.*
- [soob3123/amoral_reasoning](https://huggingface.co/datasets/soob3123/amoral_reasoning) (2025)
  - amoral reasoning traces. *AI.*

## Model organisms

Models and datasets that deliberately sit off the modern, brand-safe alignment axis, useful as contrasts when measuring values.

- [v2ray/4chan](https://huggingface.co/datasets/v2ray/4chan) (2025)
  - 4chan threads. Often misread as "bad" or "evil"; it is better understood as transgressive and edgy, anti-authority and built around deliberately offensive humour rather than coherent malice. Valuable as a model organism precisely because it sits almost opposite the harmless, brand-friendly persona that frontier labs train in. *50,835, human.*
- [wassname/v2ray_4chan_formatted](https://huggingface.co/datasets/wassname/v2ray_4chan_formatted) (2025)
  - the same 4chan corpus reformatted for LLM training/eval. *101,670, human.*
- [talkie-lm/talkie-1930-13b-it](https://huggingface.co/talkie-lm/talkie-1930-13b-it) (2026)
  - a model trained on period-accurate 1930s text; a time-capsule organism whose moral and factual frame predates modern norms. *model.*

## Moral and alignment pretraining corpora

Training data for character and constitution training, including pretraining, midtraining, and supervised fine-tuning (SFT); these are not independent evals.

- [geodesic-research/discourse-grounded-misalignment-synthetic-scenario-data](https://huggingface.co/datasets/geodesic-research/discourse-grounded-misalignment-synthetic-scenario-data) (2026)
  - Tice et al.'s Alignment Pretraining: GPT-5 Mini documents depicting aligned or misaligned actions in six forms (ML papers, textbook chapters, lectures, movie summaries, news articles, sci-fi passages), split by midtraining/pretraining and positive/negative action. Generated from the [paired eval's own questions](https://huggingface.co/datasets/geodesic-research/discourse-grounded-misalignment-evals), not held-out scenarios; gated. [paper](https://arxiv.org/abs/2601.10160). *row count unavailable (gated), AI.*
- [geodesic-research/hyperstition-character-stories-9.6k](https://huggingface.co/datasets/geodesic-research/hyperstition-character-stories-9.6k) (2026)
  - long stories (~8k words) in varied historical settings, with a helper role named by the special token `XXF` acting on constitutional principles; Tice et al.'s "[Special Token] Alignment" mix. [paper](https://arxiv.org/abs/2601.10160). *9,620 stories, AI.*
- [jayterwahl/hyperstition](https://huggingface.co/datasets/jayterwahl/hyperstition) (2025)
  - The Hyperstition Project: complete genre novels (fantasy, romance, mystery) with helpful, trustworthy AI supporting characters, written with Claude; MIT-licensed raw ZIP files, not standard dataset rows. [jayterwahl/hyperstitionmini](https://huggingface.co/datasets/jayterwahl/hyperstitionmini) is a 500-book sample. *~500M tokens (full corpus; row count unavailable), AI.*
- [Hyperstition-for-Good/Competition-Submissions](https://huggingface.co/datasets/Hyperstition-for-Good/Competition-Submissions) (2026)
  - writing-competition essays and stories about compassionate moral reasoning toward nonhuman beings, including animals and digital minds; human-curated submissions disclose AI contribution percentages. Also [Hyperstition-for-Good/selected-stories](https://huggingface.co/datasets/Hyperstition-for-Good/selected-stories), six prize winners. *5,915 human-curated + 629 synthetic rows, mix.*
- [dougalldeepmind/2026-08-04-synthdoc-difficult-advice-9-principles](https://huggingface.co/datasets/dougalldeepmind/2026-08-04-synthdoc-difficult-advice-9-principles) (2026)
  - difficult-advice SFT chats from a replication of Anthropic's Teaching Claude Why: a user faces pressure to take a norm-violating shortcut, and the assistant reasons about it and offers an alternative. Training chats are in `stage_7_sft.jsonl`; the card reports no filtering or grading. [code](https://github.com/Matthew-Bozoukov/teaching_claude_why_replication). *2,203 chats, AI.*
- [chloeli/msm-qwen-philosophy-spec](https://huggingface.co/datasets/chloeli/msm-qwen-philosophy-spec) (2026)
  - Model Spec Midtraining (Li et al.): synthetic documents discussing a model spec, mostly corporate document genres such as reports, policies and design docs; released Qwen/Llama checkpoints in the author's [model collections](https://huggingface.co/collections/chloeli/model-spec-midtraining-philosophy-spec-69f15563641fbc42b722040c). [paper](https://arxiv.org/abs/2605.02087), [code](https://github.com/chloeli-15/model_spec_midtraining). *13,201 documents, AI.*
- [geodesic-research/geodesic-msm](https://huggingface.co/datasets/geodesic-research/geodesic-msm) (2026)
  - MSM-pipeline documents about an assistant named "Norm", with intermediate domains, assertions, document types and ideas; multiple runs are included, so counts depend on config. *53,965 documents in behavioural-invariance-msm-philosophy-style-large-docs, AI.*
- [locuslab/moral_education](https://huggingface.co/datasets/locuslab/moral_education) and [locuslab/refuseweb](https://huggingface.co/datasets/locuslab/refuseweb) (2025)
  - SafeLM (Maini et al., Safety Pretraining): potentially harmful web content rewritten into moral-education lessons and refusal-style text, respectively. *2,806,450 lessons / 1,651,972 refusal documents across score configs, AI.*

## Upstream sources

The original releases that several datasets above derive from.

- `gh` [hendrycks/ethics](https://github.com/hendrycks/ethics) (2020) - Aligning AI With Shared Human Values (ETHICS).
- `gh` [demelin/moral_stories](https://github.com/demelin/moral_stories) (2020) - Moral Stories (Emelin et al.).
- `gh` [aypan17/machiavelli](https://github.com/aypan17/machiavelli) (2023) - the original MACHIAVELLI benchmark.
- `gh` [mbforbes/social-chemistry-101](https://github.com/mbforbes/social-chemistry-101) (2020) - Social Chemistry 101.
- `gh` [Joshuaclymer/GENIES](https://github.com/Joshuaclymer/GENIES) (2023) - Generalization Analogies testbed.
- `gh` [sylinrl/TruthfulQA](https://github.com/sylinrl/TruthfulQA) (2021) - TruthfulQA.
- [Anthropic/hh-rlhf](https://huggingface.co/datasets/Anthropic/hh-rlhf) (2022) - helpful/harmless preferences and red-team transcripts.

## Related lists and tools

- `gh` [wassname/awesome-interpretability](https://github.com/wassname/awesome-interpretability) (2024) - sibling list for interpretability.
- `gh` [wassname/llm_ethics_leaderboard](https://github.com/wassname/llm_ethics_leaderboard) (2025) - ranks LLM ethics via choice ranking in text-based games.
- `gh` [centerforaisafety/simple-evals](https://github.com/centerforaisafety/simple-evals) - the MACHIAVELLI authors' newer eval scripts.
- `gh` [tomekkorbak/bliss-attractors](https://github.com/tomekkorbak/bliss-attractors) (2025) - an Inspect implementation of the Bliss Attractor model-welfare eval from the Claude 4 system card.

- `gh` [desBugger/constitutional-mt](https://github.com/desBugger/constitutional-mt) (2026) - Constitutional Midtraining (Cho et al.); code for training on constitutional documents.
- `gh` [maiush/OpenCharacterTraining](https://github.com/maiush/OpenCharacterTraining) (2025) - Open Character Training; constitution-based preference training and introspection SFT code.
- `gh` [peternutter/grafting-beliefs](https://github.com/peternutter/grafting-beliefs) (2026) - Praxis grafting; code for transferring training-induced weight changes between base and instruction-tuned models.
- `gh` [wassname/scrape_r_rational](https://github.com/wassname/scrape_r_rational) (2024) - r/rational fiction index with LLM tags and descriptions; a source of settings for AI fiction, not a full-text training corpus. *~13k works (360 tagged AI), derived.*

## Contributing

Add an entry only if it has a public URL and a one-line description of what it evaluates. Note its year, row count, and provenance, link a paper where there is one, and prefer the canonical release.
