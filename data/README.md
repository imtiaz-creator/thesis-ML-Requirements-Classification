# Dataset Examples (X, y)

## Purpose

This directory contains examples of input-output pairs used for
Machine Learning based requirements classification.

## Definition of (X, y)

In this research:

**X (Input):**
Natural language software requirement statements.

**y (Output):**
The classification label assigned to each requirement.

The target classes are:

- FR = Functional Requirement
- NFR = Non-Functional Requirement


## Examples

Example 1:

X:
"The system shall allow users to create a new account."

y:
FR


Example 2:

X:
"The software shall respond to user requests within 2 seconds."

y:
NFR


## Machine Learning Process

1. Requirement text is collected.
2. Text preprocessing is applied.
3. TF-IDF converts text into numerical feature vectors.
4. Machine learning models classify requirements.
5. Performance is evaluated using Accuracy, Precision, Recall and F1-score.
