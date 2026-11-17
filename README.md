# Prompt Library — Single AI Requirements Classification Agent

- [`agent_architecture.md`](agent_architecture.md): input X, end-to-end stages, output y; implementation versus conceptual GAI extension.
- [`zero_shot.md`](zero_shot.md): one new observation X with **no** examples.
- [`few_shot.md`](few_shot.md): **the same X**, preceded by known X/y pairs from `../data/examples.csv`.

The goal is to compare **prompt strategies**, not to claim measured performance. For an actual comparison, run both prompts on the same model and record the outputs; evaluate against independently checked ground truth.
