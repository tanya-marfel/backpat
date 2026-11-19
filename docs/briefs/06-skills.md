# 06 - Agent skills

## Purpose
A portable set of SKILL.md files that run the full workflow inside Cursor or Claude Code over a local vault. This is the prototype for the app.

## Location
`skills/<name>/SKILL.md`, symlinked into `.cursor/skills/`.

## Skills
- **backpat-ingest**
  - Input: raw files (markdown, txt, vtt/srt transcripts, exported chats).
  - Output: normalized `vault/sources/*.md` with frontmatter; participant names resolved to slugs. Asks the author when a name is ambiguous.
- **backpat-extract**
  - Input: new or changed sources and a target person (or all people).
  - Output: dated, cited evidence entries appended to `evidence.md`. Duplicates are removed by source and quote.
- **backpat-voice**
  - Runs the questionnaire in [03](03-voice-profile.md), reads the samples, writes `voice.md`.
- **backpat-person**
  - Interviews the author, proposes inferred traits with citations, and writes `profile.md` per [04](04-recipient-profile.md).
- **backpat-write**
  - Input: person, template, author, optional focus or time range.
  - Output: a draft in `vault/drafts/` with inline evidence references and a list of the sources used.
- **backpat-check**
  - Flags claims not backed by evidence, generic phrasing, bias-prone wording, private data in public outputs, and drift from the author's voice. Suggests fixes.

## Requirements
- Every skill says which files it reads and writes. Every skill except `backpat-write` writes inside `vault/` only.
- No skill sends data anywhere beyond the model the user is already running.
- Skills work with the example vault out of the box.

## Acceptance criteria
- End-to-end run on the example vault: ingest, extract, voice, person, write (LinkedIn), check, with no manual file edits.
