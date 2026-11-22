# 08 - Privacy and evaluation

## Purpose
Keep sensitive third-party data safe and prove outputs are grounded, specific and in the author's voice.

## Privacy requirements
- Local-first. Nothing leaves the machine unless the user configures a hosted model.
- Redaction before hosted calls: emails, phone numbers, and optionally names of people not being written about.
- `sensitivity: private` sources never feed public templates.
- Easy deletion: removing a person deletes their folder and their index rows.
- Consent reminder when ingesting recordings. Notes on the EU AI Act for the manager use case, to be confirmed by the research in [01](01-research.md).

## Evaluation requirements
- An evaluation set in `eval/`: the example vault plus hand-written reference drafts.
- Metrics:
  - **Groundedness**: share of claims linked to valid evidence IDs (target 100%).
  - **Specificity**: concrete details per 100 words, compared with a generic baseline.
  - **Voice match**: blind preference by the author, plus style-card rule violations.
  - **Bias check**: gendered or coded adjectives (for example "abrasive", "bubbly"), applied the same way across people.
- `backpat eval` runs the checks and reports the results.

## Acceptance criteria
- Groundedness is 100% on the evaluation set. Any unsupported claim fails the run.
- No private evidence appears in public drafts.
