# 02 - Vault format

## Purpose
A single on-disk format shared by the skills and the app. Plain markdown with YAML frontmatter, readable and editable by hand.

## Layout
```
vault/
  sources/YYYY-MM-DD-slug.md
  people/<slug>/profile.md
  people/<slug>/evidence.md
  authors/<slug>/voice.md
  authors/<slug>/samples/*.md
  drafts/<person-slug>/YYYY-MM-DD-<template>.md
templates/*.md
```

## Requirements
- **Source** frontmatter: `id`, `date`, `type` (note | journal | transcript | chat | email), `participants` (person slugs), `origin` (file or app), `sensitivity` (normal | private).
- **Evidence entry** (one per observation, appended to `evidence.md`):
  ```markdown
  ### 2026-10-14 - Unblocked the billing migration
  - source: [[2026-10-14-billing-sync]]
  - quote: "I'll pair with infra tomorrow and we'll get it over the line."
  - situation: Migration stalled for two weeks.
  - behavior: Organized a pairing session and owned the follow-up.
  - impact: Shipped on time and saved the Q4 launch.
  - tags: [ownership, collaboration]
  - polarity: positive | growth
  ```
- **People** profile frontmatter: `name`, `aliases`, `role`, `relationship` (peer | report | manager | external), `since`.
- **Slugs**: lowercase and hyphenated. Aliases resolve to a single slug.
- **Drafts**: frontmatter records which template, author and evidence IDs were used.

## Open questions
- Use stable IDs per evidence entry (for example a hash) or headings? Default: short hash.
- Use wiki-links (`[[...]]`) for Obsidian compatibility? Default: yes.

## Acceptance criteria
- An example vault in `examples/vault/` with 2 people, 5 sources, 1 author.
- The app can parse every file without loss when it reads and writes it back.
