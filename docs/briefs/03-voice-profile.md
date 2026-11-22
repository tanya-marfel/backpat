# 03 - Author voice profile

## Purpose
Make drafts sound like the author, not like a generic AI. Capture style from a short questionnaire plus real writing samples.

## Requirements
- **Questionnaire** (8-10 questions, asked conversationally):
  1. How formal is your writing (1-5)?
  2. Do you prefer short and punchy or detailed and narrative?
  3. Do you use humor, emoji, exclamation marks?
  4. Phrases you often use, or would never use?
  5. How do you open and close a recommendation?
  6. How direct are you when giving critical feedback?
  7. First names or full names? "I" or "we"?
  8. Words that feel fake or corporate to you?
  9. Language and spelling variant (for example British or US)?
  10. Paste a recommendation or feedback you wrote and were proud of.
- **Samples**: 3-5 pieces of the author's own writing (messages, past reviews, posts), stored in `authors/<slug>/samples/`.
- **Output** (`voice.md`):
  - A style card: tone, sentence length, vocabulary, structure habits, phrases to use, phrases to avoid.
  - 2-3 short example excerpts for few-shot prompting.
- Supports multiple authors (for example a manager and their co-writer).
- Re-running the questionnaire updates the card instead of replacing it.

## Open questions
- Should the profile learn from accepted edits to drafts? Default: yes, as a later improvement.
- Audio voice cloning: out of scope. Covered only in research.

## Acceptance criteria
- In a blind comparison, the author picks the voice-profiled draft over a generic draft at least 4 times out of 5.
- `backpat-check` flags phrases listed under "avoid" in the style card.
