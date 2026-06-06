# Changelog

All notable changes to the AI-SDLC Framework are documented here. Format follows [Keep a Changelog](https://keepachangelog.com); versioning follows [SemVer](https://semver.org).

## [Unreleased]
- Extended the DEC-NNN schema: added a `Deferred` status and an `Amends` relation distinct from `Supersedes`; corrected DEC-006's link to `Amends` (DEC-AISDLC-012).

### Added
- Requirement-admission bar in `FRAMEWORK.md` §4 — necessity is checked when a requirement enters the SRS, not as a quality attribute; deliberate IEEE 29148 divergence (DEC-AISDLC-011).

### Changed
- Reworded the Traceable quality criterion to be bidirectional — origin plus a forward-traceable ID (DEC-AISDLC-011).

### Added
- Principle-graduation criterion in `FRAMEWORK.md` §6 — the bar a candidate clears to become a numbered principle (DEC-AISDLC-008).
- Four principles promoted from candidate to adopted: P-017, P-018, P-019, P-020 (DEC-AISDLC-009).

### Changed
- Reorganized `PRINCIPLES.md` into a chronological index plus seven thematic sections (DEC-AISDLC-010).
- Generalized the wording of P-006, P-009, P-010, and P-011 beyond their original domains (DEC-AISDLC-010).

## [0.1.1] — 2026-06-05

### Changed
- Finalized the license: Creative Commons Attribution 4.0 International (CC BY 4.0), replacing the pending placeholder from v0.1.0 (DEC-AISDLC-007).

## [0.1.0] — 2026-06-05

Initial public working draft (build-in-public).

### Added
- Markdown source-of-truth: `docs/FRAMEWORK.md`, `docs/PRINCIPLES.md`
- `docs/DECISIONS.md` — framework decision log (DEC-AISDLC-001 … 006)
- `README.md`, `CHANGELOG.md`, `LICENSE`, `.gitignore`

### Changed (hygiene)
- Retired calendar versioning (v2026-04 → v0.1.0); SemVer now applies to the framework itself
- Reconciled the decision-record schema to one canonical DEC-NNN format (DEC-AISDLC-001)
- Replaced the decision `Author` field with `Decided by` / `Drafted by` (DEC-AISDLC-006, P-019)
- Corrected principle count (15 → 16) and reconciled the project roster to registered prefixes (AISDLC, DIS, REVIQO, OOPTW)
- Aligned P-014 wording across documents to a single canonical statement

### Notes
- Candidate principles P-017 (Consistency Across the Ecosystem), P-018 (Evaluation Is the Scarce Skill), and P-019 (Keep the Human Visible) are recorded in `docs/DECISIONS.md` and slated for adoption in v0.2.0.
- Branch topology revision (DEC-AISDLC-004) and the "Necessary" requirements criterion are deferred to v0.2.0.

[0.1.0]: https://github.com/jorgevalenzuela/ai-sdlc/releases/tag/v0.1.0
