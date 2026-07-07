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

- **BL-08 — "Credit Follows Origination" (candidate).** Primary credit to the originator of an idea; the other party (human or AI) credited as support; symmetric in either direction. A genuine ethics/research area — let it accrete from real instances before crystallizing (P-001). Recorded in `DECISIONS.md`; raised in the P-019 discussion.


## Larger / later

- **BL-11 — Internal vs. public-release two-track.** Treat the framework as a product with an unstable "edge" version (carries candidate principles) and a stable tagged release (for adoption). Build-in-public, so "internal" means *unstable*, not hidden. DEC-worthy when picked up.
- **BL-12 — Existing-projects DECISIONS.md migration.** For DIS auto-ingestion (v0.3.0) to work, every project under `~/Claude-projects/` must carry `docs/DECISIONS.md` in canonical DEC-NNN format. Audit and migrate the existing ones (DIS, OOPTW, Reviqo, Faculty OS…). Prerequisite for ingestion.
- **BL-13 — Showcase app + Articles 2–3.** A later ecosystem project: an interactive guide to the framework. Its first task is reconciling the earlier 6-phase "agent pipeline" conception to the canonical 7-phase, human-in-the-loop framework (P-017). Articles 2–3 are external-articulation deliverables (Article 2 = teaching artifact for P-012).
- **BL-15 — Audit the framework through design principles/patterns (lens, not mold).** Read AI-SDLC itself through SOLID and GoF patterns to *name and stress-test* the architecture it already has — not to impose new structure. Diagnostic lens only: keep a pattern when it names something the framework already grew; drop it when it adds structure for elegance's sake (over-engineering / theorizing, against P-001 & P-015). Starting observations: DIP already lives in P-017 (depend on conventions, not implementations); Strategy in P-009/P-010 (pick the mechanism that fits); Template Method now adopted for the lifecycle. This is P-013 (audit design against SOLID) turned on the framework itself — P-008 dogfooding. *(Raised at the end of the v0.2.0 lifecycle-revisit session.)*
- **BL-16 — Per-gate verification spec (operationalize P-014).** P-014 promises a per-phase map of *what to verify + what competency it takes to approve*; that artifact was never written. Assemble it as `GATES.md` or FRAMEWORK §9. Requirements gate is fully specified content (§4: 6 quality criteria + 3-part admission) but not assembled as a checklist; Design gate has dimensions (P-013: SOLID/coupling/cohesion) but no pass rubric; Development has **no** code-inspection gate at all. Only Design (Phase 2) and Deployment (Phase 7) are formally named gates today. *(Raised when Jorge asked what's verified at each approval point, S03.)*
- **BL-17 — DEC schema: mark a Consequences item as *deferred scope* vs *informational note*.** Distinct from BL-09/BL-10 (both resolved) — this tags items *inside* the Consequences field, so a deferred cleanup is legible as owed scope, not a note. Direct implication of P-022. Target the v0.3.0 schema pass. *(From DEC-AISDLC-018 / P-022.)*
- **BL-18 — Phase 3 reconfiguration element: "review pending cleanup from prior iterations."** Add as a Project Configuration reconfiguration element so deferred cleanup is picked up at iteration boundaries. *(From P-022 — scheduled per the principle itself, not deferred silently.)*
- **BL-19 — Adopt P-023 "Pin and Provide" + `CLAUDE.md` retrofit.** Each project declares the framework version it adopts and provides access to that version's artifacts (a `CLAUDE.md` root pointer naming the pinned version + repo link). Retrofit existing projects. **Coordinate with BL-12** — both are "touch every project" passes; do the `CLAUDE.md` add and the `DECISIONS.md` migration in one sweep. Origin: the S03 collision itself — the Reviqo proposal mis-numbered its own principles because it had no authoritative pin (the failure P-023 fixes, demonstrated live).
- **BL-20 — Adopt P-024 "Iteration Closure Gates Release" + evaluate 9→10 phase split.** Two closure points (engineering vs full iteration), pre-release `-rcN` tag convention, and splitting Reflect into Development Reflect + Overall Reflect. **Reference the existing voiding model (DEC-AISDLC-013) — do not redocument it**; P-024's genuinely-new content is the tag convention, the two closure points, and the phase split, not the voiding mechanics. The split re-anchors FRAMEWORK §6 (which names Reflect-as-Phase-8 as where principles graduate) — decide which Reflect graduates principles. Its own session.
- **BL-21 — Cross-project consistency (P-017): Reviqo REVIQO-012 P-021 reference.** REVIQO-012 cites "P-021" meaning Iteration Closure; framework P-021 is "Define by the Whole Boundary." Once P-024 is adopted, update REVIQO-012 to point at P-024. *(Reviqo committed to follow framework wording per REVIQO-012.)*
- **BL-22 — Bureaucracy assessment → v0.4.0 scope.** Proposal §4. After v0.3.0 ships additions, assess net process weight: **principle audit** (load-bearing vs descriptive — ties into BL-06 tiering and BL-07 scope axis), possible **phase consolidation** (Release + Deployment?), **iteration sizing** (small/medium/large, where size declaration justifies default voids), **voiding-cost tightening**, and **solo vs team scaling**. Keep separate from v0.3.0 so net weight stays legible (don't add + prune in one release).
- **BL-23 — Code review as a first-class phase (candidate → next free number, ~P-025).** Elevate code review from a Phase-4 Definition-of-Done item to its own phase: bug-catching beyond tests, and *ownership transfer* — the moment a human takes ownership of code they didn't type (P-018 in practice). Open questions: phase placement (between Development and Testing, or inside Testing), approval-gate semantics for solo work. **Deferred until after BL-22** — its placement and weight should reflect a leaner framework. *(Proposal §2.)*
- **BL-24 — Hygiene: update project instructions + Context Document to v0.2.0.** Both still describe v0.1.0 (7 phases, 16+1 principles, old single `Author` DEC field). Bring them to 9 phases (0–8), 21 principles, and the `Decided by`/`Drafted by` schema (DEC-006). Recurring: fresh conversations load the stale set on startup — this is the motivating case for BL-19 (P-023).

## Loose ends to verify

- **BL-14 — Pre-1.0 SemVer note.** Confirm `FRAMEWORK.md` §6 states the 0.x convention (minor versions may break before 1.0); add the one-liner if it didn't land. (An A-hygiene item from v0.1.0 that may have slipped.)

---

*AI-SDLC Framework · `BACKLOG.md` · parked work, written down so it survives the session (P-002)*
