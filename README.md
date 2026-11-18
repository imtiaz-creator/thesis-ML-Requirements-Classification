# Implementation notes

This folder intentionally does not include a fabricated trained classifier or fake API responses. To implement the end-to-end agent:

1. Load the saved TF-IDF vectorizer fitted on the training split of PROMISE_exp.
2. Load the trained and selected SVM or Random Forest model.
3. Accept one requirement string X and apply exactly the same preprocessing used at training time.
4. Obtain the actual `FR`/`NFR` prediction and return it as y.
5. Optionally call a configured LLM for a brief *advisory* explanation, ensuring the LLM does not silently change y.

The `.md` prompts in `/prompts/` can be run in an LLM interface without requiring these artifacts. That is a **prompting demonstration**, not the original model's inference.
## Lab 1.5 — End-to-End AI Demonstration

The Google Colab notebook demonstrates the
AI Requirements Classification Agent using
the Gemini API.

[View Lab 1.5 Google Colab Notebook](notebooks/Lab_1_5_Gemini_AI_Agent.ipynb)

### Lab 1.5 — Reflection

The developed AI Requirements Classification Agent demonstrates an end-to-end solution for automatically classifying natural-language software requirements into Functional Requirements (FR) and Non-Functional Requirements (NFR). The system receives a software requirement as input X and processes it through data understanding, reasoning, inference, and output generation to produce the predicted classification y. Google Colab was used as the development and execution environment, while the Gemini API provided the generative AI capabilities for analyzing and classifying requirements. The Gemini API key was securely managed using Google Colab Secrets instead of being hardcoded into the notebook. Two prompt engineering techniques from Lab 1.4, zero-shot and few-shot prompting, were integrated into the system. The zero-shot approach classified a new requirement without examples, while the few-shot approach used five previously labelled FR/NFR examples to guide classification. Both prompting methods successfully classified the 99.9% system availability requirement as NFR and generated supporting explanations. One strength of the implementation was the successful integration of Gemini with a structured and reproducible prompting workflow. However, the demonstration was limited to one evaluation requirement, and the original thesis's SVM and Random Forest models were not executed as part of the Gemini-based pipeline. Future improvements could include testing a larger requirements dataset, comparing Gemini with the classical machine learning models, and evaluating prediction consistency and overall classification accuracy.
