# 07 - Local-first app

## Purpose
A standalone tool that does what the skills do, without needing an AI code editor, and adds audio transcription, indexing and a review UI.

## Requirements
- **CLI** (Python, Typer): `backpat ingest | extract | voice | person | write | check | status`.
- **Storage**: the markdown vault is the source of truth. A SQLite index is used for search, deduplication and an evidence timeline, and is rebuildable from the vault.
- **Models**: provider-agnostic through LiteLLM (Anthropic, OpenAI, Ollama). Per-command model choice. Local model by default for extraction of private sources.
- **Audio**: faster-whisper transcription. Optional pyannote speaker identification, with speakers mapped to people slugs.
- **Prompts**: shared with the skills (single source in `prompts/`), so the two never drift apart.
- **Later**: a desktop or local web UI (Tauri, or FastAPI with a simple frontend) with:
  - An evidence timeline per person.
  - Side-by-side draft and sources, with click-to-source citations.
  - Accept or edit drafts, with edits fed back into the voice profile.
  - Importers for meeting tools and notes apps chosen in [01](01-research.md).

## Open questions
- Python or TypeScript? Default: Python, for the transcription ecosystem.
- Packaging: pipx first, a desktop installer later.

## Acceptance criteria
- `backpat` produces the same drafts as the skills on the example vault (within model variance).
- Works fully offline with Ollama.
