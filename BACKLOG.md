# AI-SDLC — Backlog

`BACKLOG.md` · AI-SDLC Framework · parked / deferred work

Items deliberately deferred — not yet scheduled, recorded here so they survive beyond any single working session (P-002: write it down, don't rely on memory). Each notes *what it is*, *why it's parked*, and *where it came from*, so it reads cold. When an item is picked up and decided, it graduates to a DEC entry in `DECISIONS.md` and leaves this list.

---

## Open principle & structure refinements
*(from the v0.2.0 principle review — single-responsibility audit)*

- **BL-01 — Split P-005.** "Validate Interaction Before Optimizing Performance" carries two ideas: *sequencing* (validate before you optimize) and *separation of concerns* (isolate UI from infrastructure). SRP flag — consider splitting into two principles.
- **BL-02 — Split P-017.** "Consistency Across the Ecosystem" bundles the consistency mandate **and** the convention-vs-implementation boundary + "does uniformity create value" test. The boundary may deserve its own principle (it originated in DEC-AISDLC-004).
- **BL-03 — §5 cohesion.** The section "Versioning, consistency & production" bundles three themes — versioning (P-011), runtime safety (P-016), cross-project governance (P-017). Re-section when convenient; the three-noun name is the tell.
- **BL-04 — §4 cohesion.** "Design & iteration" is a broad design bucket (order, communication, fit, tool choice, scope). Looser than ideal; revisit if it grows.
- **BL-05 — P-016 review.** Jorge has an unraised flag on P-016 ("Production Guardrails Need Multiple Independent Layers") — likely generalizing its LLM-specific examples, parallel to the P-009 reword. Raise and resolve.

## Axes to formalize (framework meta-structure)

- **BL-06 — Normative-strength tiering.** Classify guidance into **rules / principles / guidelines** (firm → advisory). Decide sections-vs-separate-documents by whether the tiers are *consumed differently* (a rule a tool could check vs. a guideline that only advises). Touches all principles — a later version.
- **BL-07 — Scope-of-applicability axis.** Mark principles **universal vs. contextual** (e.g., P-008 is contextual). Currently handled ad hoc by the §7 scope note; full per-principle treatment deferred. Orthogonal to theme and to BL-06.

## Candidate principles & schema

- **BL-08 — P-021 "Credit Follows Origination" (candidate).** Primary credit to the originator of an idea; the other party (human or AI) credited as support; symmetric in either direction. A genuine ethics/research area — let it accrete from real instances before crystallizing (P-001). Recorded in `DECISIONS.md`; raised in the P-019 discussion.
- **BL-09 — DEC schema: `Deferred/Parked` status.** The Status enum (Proposed/Accepted/Rejected/Superseded) has no value for a parked decision (DEC-AISDLC-004 wanted one). Add in a schema revision.
- **BL-10 — DEC schema: `Amends` vs `Supersedes`.** `Supersedes` is currently used for partial amendments (DEC-006 amended only DEC-001's authorship). Consider a distinct `Amends` relation for partial changes.

## Larger / later

- **BL-11 — Internal vs. public-release two-track.** Treat the framework as a product with an unstable "edge" version (carries candidate principles) and a stable tagged release (for adoption). Build-in-public, so "internal" means *unstable*, not hidden. DEC-worthy when picked up.
- **BL-12 — Existing-projects DECISIONS.md migration.** For DIS auto-ingestion (v0.3.0) to work, every project under `~/Claude-projects/` must carry `docs/DECISIONS.md` in canonical DEC-NNN format. Audit and migrate the existing ones (DIS, OOPTW, Reviqo, Faculty OS…). Prerequisite for ingestion.
- **BL-13 — Showcase app + Articles 2–3.** A later ecosystem project: an interactive guide to the framework. Its first task is reconciling the earlier 6-phase "agent pipeline" conception to the canonical 7-phase, human-in-the-loop framework (P-017). Articles 2–3 are external-articulation deliverables (Article 2 = teaching artifact for P-012).

## Loose ends to verify

- **BL-14 — Pre-1.0 SemVer note.** Confirm `FRAMEWORK.md` §6 states the 0.x convention (minor versions may break before 1.0); add the one-liner if it didn't land. (An A-hygiene item from v0.1.0 that may have slipped.)

---

*AI-SDLC Framework · `BACKLOG.md` · parked work, written down so it survives the session (P-002)*
