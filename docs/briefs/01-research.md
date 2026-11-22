# 01 - Deep research

## Purpose
Validate the opportunity and choose technical approaches before investing in the app. The deliverable is `docs/research.md`.

## Requirements
- **Market and competitors**
  - HR suite AI writers: Lattice, Culture Amp, 15Five, Leapsome, Betterworks.
  - Feedback and recognition bots: Windmill, Confirm, Bonusly.
  - Meeting tools with summaries: Granola, Otter, Fireflies, Fathom, Zoom AI Companion, Google Meet Gemini notes.
  - Ad-hoc use of ChatGPT or Claude.
  - Identify the gap: cross-source, personal, persistent evidence, author voice.
- **Source access**
  - For each source, compare export formats with API availability: Granola, Otter, Fireflies, Zoom, Google Meet, Notion, Obsidian, Day One, Apple Notes, Slack, email.
  - Local transcription (whisper, faster-whisper, whisper.cpp) and speaker identification ("diarization", for example pyannote).
- **Legal and ethics**
  - GDPR: processing third-party personal data, legitimate interest, retention.
  - Recording-consent laws (one-party versus all-party consent).
  - EU AI Act: AI used by employers for performance evaluation is high-risk (Annex III). Assess what this means for the manager use case.
  - Disclosure norms for AI-assisted recommendations (including LinkedIn policy).
- **Technical approaches**
  - Long-context prompting versus retrieval versus incremental extraction into an evidence log.
  - Matching the same person across sources when names and aliases vary.
  - Voice transfer: a style card plus few-shot examples, compared with fine-tuning.
  - Local models (Ollama, LM Studio) versus hosted APIs: quality, cost, privacy.
  - Evaluation methods: groundedness, specificity, voice match, bias.
- **Business**: positioning, pricing ideas, distribution (skills marketplace, open source, paid app), top risks.

## Open questions
- Is audio voice cloning (reading drafts aloud in the author's voice) in scope? Default: research only.
- Is the target region EU-only first, or global?

## Acceptance criteria
- `docs/research.md` covers every section above and cites its sources.
- Ends with a recommendation section that feeds back into specs 02-08.
