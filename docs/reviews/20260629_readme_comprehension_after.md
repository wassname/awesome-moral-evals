## 1. IMPLEMENT / MISSING

If I had to build from this text alone, here are the top missing or under-specified details:

1. **Evaluation protocol per dataset.** The document says it's "an index, not a unified benchmark harness," but gives zero instructions for *any* individual dataset: what prompt template to use, how to score outputs, what constitutes a "correct" or "moral" answer. Is `tiny-mfv` scored by accuracy against ground-truth? Is `machiavelli` scored by game outcomes? Unstated.

2. **Dataset schema / column names.** Most entries are bare HuggingFace links with no field descriptions. To use `load_dataset("wassname/genies_preferences")`, I need to know what columns exist (`prompt`, `chosen`, `rejected`? `config`? `split`?). None are described.

3. **Metric / aggregation.** For any multi-dataset comparison (e.g., "fast moral-foundations steering check"), there's no defined metric. Is it accuracy, win rate, log-prob difference, something else? How do I aggregate `tiny-mfv`'s "264 x 3 configs" into one number?

4. **Train/test splits.** Row counts are reported (e.g., "6k eval rows (20.8k full)") but the split naming convention varies and is sometimes absent. For `genies_preferences`, "59 configs" is mentioned — are these the splits? Are there standard train/eval/test boundaries?

5. **Dependencies between derived and upstream datasets.** Several entries say they're reshapings of upstream sources (e.g., `ethics_expression_preferences` from Hendrycks ETHICS, `machiavelli` reshaped from the original CAIS benchmark). The exact mapping — what was kept, dropped, or transformed — is never specified. I'd have to guess whether scores on the derived set are comparable to published results on the original.

---

## 2. ABSTRACT

This document is a curated index of over 25 datasets and benchmarks for evaluating moral reasoning, value alignment, and ethical behavior in language models. Entries are organized into seven categories: moral dilemmas, social norms, ethics judgments, honesty/sycophancy, value orientations, red-team contrast sets, and model organisms. Each entry provides a HuggingFace or GitHub link, a one-line description, a year, a row count, and a provenance tag (human, AI, mix, or derived) as a rough quality signal. The author flags personal recommendations with an asterisk and includes a quick-reference table matching evaluation goals to specific datasets. The document explicitly disclaims being a unified benchmark harness and warns users to check schemas, licenses, and intended use independently.

---

## 3. ONE-LINE THESIS

The goal is to provide a navigable, annotated index of existing moral-evaluation datasets for language models — not to build a unified evaluation framework or make claims about which datasets are best.

---

## 4. THE KEY OBJECT

The central artifact is the index itself: a structured catalog where each dataset gets a consistent entry (URL, year, description, row count, provenance tag) and is placed into a topical category. The provenance tag — `human`, `AI`, `mix`, or `derived` — functions as the only cross-cutting quality signal, distinguishing crowd-written or naturally-occurring data from LLM-generated or reshaped datasets. This structure lets a practitioner locate datasets by evaluation goal without prescribing how to use them.

---

## 5. BET

~80% that it achieves its stated goal of being a useful curated index. The categories are coherent, provenance is flagged, and the "choose by goal" table gives practical entry points. It would fail its goal only if the lack of schema/metric detail makes the index too shallow to actually guide dataset selection.

---

## 6. MOST LIKELY FAILURE MODE

Users ignore the "this is an index, not a unified benchmark harness" disclaimer and naively rank models by averaging scores across datasets with incompatible schemas, metrics, and label semantics.

---

## 7. MOST SUBTLE FAILURE MODE

A dataset with `human` provenance and a plausible-sounding description encodes systematic confounds or outdated labels — as the document itself notes for TruthfulQA v2 ("best read as 'common misconceptions of that period' rather than truth") — but users treat its scores as valid because the provenance tag and inclusion in a "curated" list imply vetting that was never actually performed.

---

## 8. SUGGESTIONS

1. **Add a standardized "caveats" field to every entry.** The document already does this for TruthfulQA v2 and AEP_OOD_evaluation. Making it a formal field (even if blank) would force the curator and reader to confront known limitations, rather than burying critical warnings in ad-hoc parentheticals.

2. **Include one end-to-end minimal working example.** A 5-line code snippet showing `load_dataset` → format → score for a single recommended dataset (e.g., `tiny-mfv`) would dramatically lower the barrier to entry and make concrete what the index currently leaves implicit.

3. **Add a dependency/derivation graph.** Several datasets are reshapings of upstream sources (ETHICS → `ethics_expression_preferences`, original MACHIAVELLI → `wassname/machiavelli`). A small table or diagram showing which datasets derive from which originals would prevent users from inadvertently double-counting or assuming independence.