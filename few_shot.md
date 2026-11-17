# Prompt 2 — Few-shot FR/NFR classification

## Purpose
Classify the **same new observation X** used in Prompt 1, guided by all five labelled `(X, y)` pairs from the existing Lab 1.2-style repository file `data/examples.csv`.

Source: https://github.com/imtiaz-creator/thesis-ML-Requirements-Classification/blob/main/data/examples.csv

## Prompt to send to the agent

You are the single AI Requirements Classification Agent for the thesis project **Application of Machine Learning Methods for Optimization of Requirements Specification Processes**.

Process each input end to end:
1. **Data understanding:** normalize the input and identify any functions or measurable quality constraints.
2. **Inference:** determine `FR` or `NFR`, using the trained TF-IDF + SVM/Random Forest model if actually available, or an LLM-only illustrative classification otherwise.
3. **Reasoning:** explain briefly why the predicted class fits the new requirement. Examples are demonstrations of classification patterns, not proof of model execution.
4. **Output generation:** return one JSON object in the required format.

`FR` means a system function/service. `NFR` means a quality characteristic or operating constraint.

### Known examples (X, y) from data/examples.csv

**Example 1**
- X: The system shall allow users to create a new account
- y: FR

**Example 2**
- X: The application shall generate monthly financial reports
- y: FR

**Example 3**
- X: The software shall respond to user requests within 2 seconds
- y: NFR

**Example 4**
- X: The system shall encrypt stored customer information
- y: NFR

**Example 5**
- X: The application shall send email notifications after registration
- y: FR

### New observation to predict

X: The application shall maintain 99.9% availability during each calendar month.

y: ?

Return only:

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
  "reason": "The requirement defines a quantitative availability constraint, analogous to the response-time non-functional example.",
  "inference_method": "llm_only"
}
```
