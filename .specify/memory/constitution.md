# Backpat Constitution

## Core Principles

### I. Evidence Over Generation (NON-NEGOTIABLE)
- Every factual claim in a draft MUST cite at least one evidence entry, and every evidence
  entry MUST link to a dated source in the vault.
- The system MUST NOT invent achievements, quotes, metrics or events. If evidence is missing,
  the draft MUST say so or omit the claim.
- Evidence MUST accumulate in a per-person log over time. Drafts are built from that log, not
  from a one-off summary of raw sources.

Rationale: generic or invented praise is the main failure of AI-written feedback; citations make
every sentence checkable.

### II. Local-First, Private by Default
- The markdown vault on the user's machine is the source of truth. Any database or index MUST be
  rebuildable from the vault.
- No data leaves the machine unless the user has explicitly configured a hosted model.
  Every hosted call MUST first redact contact details (emails, phone numbers) and SHOULD redact
  names of people who are not the subject.
- Telemetry, analytics and cloud sync MUST be off by default and opt-in only.

Rationale: sources contain sensitive third-party data that the subject never agreed to share.

### III. Audience Boundaries
- Every source and evidence entry carries a sensitivity level (`normal` or `private`).
- Evidence marked `private` MUST NOT appear in outputs whose audience is `public` (for example
  LinkedIn recommendations or reference letters).
- Growth or critical feedback MUST only be produced by private-audience templates.

Rationale: a single leaked journal line in a public recommendation destroys trust in the tool.

### IV. Voice and Recipient Shape Tone, Never Facts
- The author's voice profile and the recipient's profile MAY change wording, structure, length
  and framing. They MUST NOT add, remove or alter facts drawn from evidence.
- Traits inferred about a recipient MUST be marked `inferred`, cite their source, and be
  confirmed by the author before they are saved to a profile.

Rationale: personalization is the product's value, but it must never become fabrication.

### V. Human in the Loop
- Backpat produces drafts only. It MUST NOT send, post or submit anything on the user's behalf.
- Every draft MUST show its citations so the author can verify each claim before using it.
- Backpat MUST NOT score, rank or compare people, or recommend employment decisions.

Rationale: the author stays accountable for what they sign, and decision support stays outside
high-risk automated evaluation.

### VI. One Vault, One Prompt Set
- The agent skills and the app MUST read and write the same vault format and use the same prompt
  files from a single location.
- Any change to the vault format MUST be versioned and include a migration for existing vaults.

Rationale: the skills are the prototype for the app; drift between them doubles the work and
breaks users' vaults.

### VII. Simplicity First
- Prefer plain markdown, small scripts and existing tools over new services or infrastructure.
- A new dependency, storage layer or integration MUST be justified in the feature plan against a
  simpler alternative.
- Build the skills first and add app features only when the skills prove the workflow.

Rationale: an early, solo-built product wins by shipping a working loop, not by architecture.

## Data, Consent and Compliance Constraints

- Ingesting recordings or transcripts MUST show a consent reminder. Backpat MUST NOT encourage
  recording people without their knowledge.
- Deleting a person MUST remove their vault folder, their evidence, their drafts and any index
  rows, leaving no copy behind.
- Data handling MUST support GDPR expectations: data minimization, a clear purpose, and deletion
  on request.
- Manager-facing features are decision support for writing only, as set out in Principle V.
  Any feature that could fall under high-risk use in the EU AI Act (Annex III, employment)
  requires an explicit constitution amendment before it is specified.
- Language checks MUST flag gendered or coded adjectives and apply the same rules to every person.

## Development Workflow and Quality Gates

- Features follow the Spec Kit cycle: specify, clarify, plan, tasks, implement, converge.
  Every plan MUST include a Constitution Check against Principles I to VII.
- An example vault (`examples/vault/`) MUST exist and every skill and command MUST run end to end
  on it.
- Release gates, enforced by `backpat-check` and later `backpat eval`:
  - Groundedness: 100% of claims in evaluation drafts cite valid evidence. Any unsupported claim
    fails the gate.
  - Audience leak: zero private evidence in public drafts.
  - Bias: no flagged wording left unresolved in evaluation drafts.
- Prompt or template changes MUST be re-run against the evaluation set before merge.

## Governance

- This constitution overrides other project practices and briefs. Where a brief in
  `docs/briefs/` conflicts with it, the constitution wins.
- Amendments are made by editing this file with a Sync Impact Report, through a reviewed commit
  or pull request, with dependent specs updated in the same change.
- Versioning follows semantic versioning:
  - MAJOR: a principle is removed or redefined.
  - MINOR: a principle or section is added or materially expanded.
  - PATCH: clarifications and wording changes.
- Every `/speckit-plan` and `/speckit-converge` run MUST verify compliance. Any justified
  exception MUST be recorded in the plan's complexity tracking with a reason and a simpler
  alternative that was rejected.
- Runtime guidance for agents lives in `docs/briefs/` until each feature's spec replaces it.

**Version**: 1.0.0 | **Ratified**: 2026-11-22 | **Last Amended**: 2026-11-22
