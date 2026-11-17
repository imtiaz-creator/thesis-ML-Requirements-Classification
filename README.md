# Implementation notes

This folder intentionally does not include a fabricated trained classifier or fake API responses. To implement the end-to-end agent:

1. Load the saved TF-IDF vectorizer fitted on the training split of PROMISE_exp.
2. Load the trained and selected SVM or Random Forest model.
3. Accept one requirement string X and apply exactly the same preprocessing used at training time.
4. Obtain the actual `FR`/`NFR` prediction and return it as y.
5. Optionally call a configured LLM for a brief *advisory* explanation, ensuring the LLM does not silently change y.

The `.md` prompts in `/prompts/` can be run in an LLM interface without requiring these artifacts. That is a **prompting demonstration**, not the original model's inference.
