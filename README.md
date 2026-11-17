# AI Requirements Classification Agent — Prompt Examples

This directory documents two prompting examples for the master's thesis **Application of Machine Learning Methods for Optimization of Requirements Specification Processes**.

## Repository layout

```
thesis-ML-Requirements-Classification/
├── data/
│   └── examples.csv            # Pre-existing labelled examples
└── prompts/
    ├── README.md
    ├── zero_shot.md            # Prompt 1: single unseen X, no examples
    └── few_shot.md             # Prompt 2: same X with five known (X,y) pairs
```

## Thesis-aligned conceptual pipeline

**Input X**: a natural-language software requirement.

**Single agent A** orchestrates these stages:
1. **Data understanding** — validate, clean and normalize requirement text.
2. **Inference** — TF-IDF feature extraction and the trained SVM or Random Forest model predict `FR` or `NFR`.
3. **Reasoning** — an LLM may generate a short explanation conditioned on the input requirement and predicted category.
4. **Output generation** — return structured `y = {predicted_y, reason, inference_method}`.

**Output y**: FR/NFR prediction with a concise explanation and an honest inference-method label.

> The existing thesis prototype evaluates classical ML classification. LLM reasoning is a conceptual extension, not an experimentally evaluated feature of that prototype. Running these examples with a general LLM alone does not invoke the thesis ML classifier.

## Example provenance

The five labelled pairs in `few_shot.md` were copied from the existing repository file: [`data/examples.csv`](../data/examples.csv) (GitHub main branch, reviewed 2026-11-17). They are not fabricated. The new observation about 99.9% availability does not appear among those five examples. Prompt 1 and Prompt 2 deliberately use the same new observation for a controlled comparison.

## How to run

1. Open `zero_shot.md` and copy the **Prompt to send to the agent** into your LLM chat or an agent implementation.
2. Record the returned JSON and whether the inference came from an actually executed trained ML model or LLM-only reasoning.
3. Repeat using `few_shot.md` with the same observation X.
4. Compare the predicted label and explanation. Do not claim improved accuracy from a single example; evaluate on a held-out labelled test set before reporting performance differences.

## Interpretation

- `FR`: functionality or service the software must provide.
- `NFR`: quality property, constraint, performance, security, or availability requirement.
- `inference_method = trained_ml` only when the actual thesis model has been invoked.
- `inference_method = llm_only` for prompt-only demonstrations.

## Notes

Few-shot examples can influence LLM predictions, but do not retrain SVM/Random Forest models. For fair ML evaluation, prevent train/test leakage and keep held-out evaluation observations separate from examples used in prompts.
