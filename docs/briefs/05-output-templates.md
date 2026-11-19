# 05 - Output templates

## Purpose
Define what each output type should look like. Templates are user-editable markdown files.

## Template types
- `linkedin-recommendation`: 80-200 words, third person, relationship line first, 1-2 concrete stories.
- `peer-feedback`: strengths plus growth areas, each item as situation, behavior, impact.
- `manager-review`: organized by competency or ladder level, with an evidence count per competency, plus a summary and next-period goals.
- `kudos`: 1-3 sentences for Slack or email, one specific moment.
- `reference-letter`: formal, with context, capabilities, and an endorsement level.
- `growth-feedback`: private, matched to the recipient's feedback preference, with actionable suggestions.

## Template file format
```markdown
---
id: linkedin-recommendation
audience: public
length: { min: 80, max: 200, unit: words }
perspective: third-person
evidence: { min: 2, polarity: [positive] }
---
## Structure
1. Relationship and context
2. Story 1 (strongest evidence)
3. Story 2 or a trait pattern
4. Endorsement
## Rules
- No claims without evidence IDs.
- No internal confidential details (public audience).
```

## Requirements
- Template frontmatter controls: audience (public | private | internal), length, perspective, evidence filters, tone overrides.
- Public templates automatically exclude evidence marked `sensitivity: private`.
- Users can copy and edit templates, or add new ones.

## Acceptance criteria
- Each of the six templates produces a valid draft from the example vault.
- Drafts respect length limits and audience filters.
