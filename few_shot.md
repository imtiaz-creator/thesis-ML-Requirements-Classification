# Prompt 2 — Few-Shot FR/NFR Classification

**Purpose:** classify the **same unseen X** as Prompt 1, but include five known `(X, y)` examples from `../data/examples.csv`.

## Prompt to send to the agent

```text
You are the single AI Requirements Classification Agent for a thesis project
on optimizing software requirements specification processes.

Input X is a natural-language software requirement.
Process it end to end:
1. Data understanding: identify functions versus qualities/constraints.
2. Inference: use the labelled pairs as guidance and determine FR or NFR.
3. Reasoning: explain your classification briefly. Do not falsely claim
   that an SVM or Random Forest model was executed.
4. Output generation: return exactly the requested fields.

Known examples (X, y):
X: "The system shall allow users to create a new account."
y: FR

X: "The application shall generate monthly financial reports."
y: FR

X: "The software shall respond to user requests within 2 seconds."
y: NFR

X: "The system shall encrypt stored customer information."
y: NFR

X: "The application shall send email notifications."
y: FR

Now classify this NEW requirement; it is not one of the examples:
X: "The application shall maintain 99.9% availability during each calendar month."

Output format:
y: FR or NFR
explanation: one sentence
```

## Expected answer (human-labelled illustration)

```text
y: NFR
explanation: The requirement sets a measurable service availability constraint.
```

**Source:** The five labelled examples are transcribed into `../data/examples.csv` from prior lab content provided in the conversation. Verify exact wording against your own Lab 1.2 CSV.
