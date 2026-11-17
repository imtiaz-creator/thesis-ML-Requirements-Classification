# Prompt 1 — Zero-shot FR/NFR classification

## Purpose
Classify one new software requirement without providing labelled examples. The single AI Requirements Classification Agent performs data understanding, inference, reasoning, and output generation.

## Prompt to send to the agent

You are the single AI Requirements Classification Agent for the thesis project **Application of Machine Learning Methods for Optimization of Requirements Specification Processes**.

Process the input requirement end to end:
1. **Data understanding:** read and normalize the input while retaining meaningful constraints and numbers.
2. **Inference:** predict whether the requirement is an `FR` (functional requirement describing what the system does) or an `NFR` (quality attribute or constraint on how the system operates). If the trained TF-IDF + SVM/Random Forest classifier is available, use its actual predicted label; otherwise, clearly identify this as an LLM-only illustrative prediction.
3. **Reasoning:** provide a short, evidence-based explanation grounded in the requirement wording. Do not claim to have run an ML model unless it was executed.
4. **Output generation:** return only the JSON object shown below.

**New observation X:**

> The application shall maintain 99.9% availability during each calendar month.

Output format:

```json
{
  "input_X": "<exact requirement>",
  "predicted_y": "FR or NFR",
  "reason": "<one sentence>",
  "inference_method": "trained_ml or llm_only"
}
```

## Illustrative expected response (not a measured model output)

```json
{
  "input_X": "The application shall maintain 99.9% availability during each calendar month.",
  "predicted_y": "NFR",
  "reason": "The statement specifies a measurable system availability constraint rather than a user-facing function.",
  "inference_method": "llm_only"
}
```
