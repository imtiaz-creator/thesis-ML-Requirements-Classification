# Single AI Agent — End-to-End Conceptualization

## Thesis mapping

**Title:** Application of Machine Learning Methods for Optimization of Requirements Specification Processes.

**Agent:** AI Requirements Classification Agent (one orchestrating controller).

**Input `X`:** one natural-language software requirement.

**Output `y`:** a class label, `FR` or `NFR`. A richer application response can additionally contain an explanatory note, but the core prediction is the FR/NFR label.

## End-to-end pipeline

1. **Data understanding:** receive `X`; validate it is a requirement statement; normalize whitespace, lowercase and remove punctuation for the classical ML path while retaining relevant numbers.
2. **Inference:** transform the cleaned text with the **fitted TF-IDF vectorizer**; obtain a label using the **trained SVM or Random Forest classifier**. The agent reports the classifier's actual output, not an invented prediction.
3. **Reasoning (proposed GAI layer):** an LLM may be given the original X and predicted class to explain what makes the statement functional or non-functional. LLM explanations are advisory; they do not overwrite the predicted class silently.
4. **Output generation:** return `y = FR` or `y = NFR`, and optionally a concise explanation. A human analyst can review the result.

## Formula

`y = A(X)`, where `A` is the single controller coordinating `preprocess → TF-IDF → classifier` and optionally LLM-generated explanation.

## Illustrative example (not a model execution)

**X:** "The software shall respond to user requests within 2 seconds."

**Expected y:** `NFR` (performance constraint).

**Example explanation:** "The requirement sets a measurable response-time quality constraint."

## Architecture boundaries

- **In the thesis:** PROMISE_exp labelled data, FR/NFR classes, preprocessing, TF-IDF, SVM/Random Forest, and quantitative evaluation.
- **Proposed only:** autonomous agent orchestration as a product interface and LLM explanation/refinement.
- **Not claimed:** that an external LLM API has been connected, that live predictions are available, or that the LLM improved accuracy.

See `../diagrams/single_agent_activity.puml` and `../diagrams/single_agent_component.puml`.
