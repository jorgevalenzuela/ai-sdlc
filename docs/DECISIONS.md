# AI-SDLC — Decision Log

`docs/DECISIONS.md` · AI-SDLC Framework · v0.1.0

## Purpose

This document is the running record of the significant engineering decisions made while building the AI-SDLC Framework — each captured with its context, the alternatives weighed, and the consequences, so the *reasoning* behind a choice survives the choice itself (P-002). As the framework evolves in public, new decisions are appended here in DEC-NNN format, and each decision's real-world **Outcome** and **Lesson Learned** are filled in later — turning the log into the raw material from which new principles are extracted (P-001) and from which other projects in the ecosystem inherit conventions (P-017).

### What this is *not*

- **Not a changelog.** Release-by-release changes live in `CHANGELOG.md`, tied to SemVer.
- **Not a backlog or task list.** Planned work is tracked elsewhere.
- **Not framework documentation.** How AI-SDLC works is in the Context Document; this log records *choices*, not instructions.
- **Not a record of every choice — only significant ones.** What counts as "significant" is the engineer's, manager's, or team's call; AI may flag candidates when it spots them. AI-SDLC doesn't impose a universal bar — it simply makes the discipline of capturing whatever *you* judge significant deliberate (P-003). See DEC-AISDLC-005.

## Conventions

- **ID** — per-project prefix + zero-padded sequence. Registered prefixes: `AISDLC`, `DIS`, `REVIQO`, `OOPTW`.
- **Status** — Proposed · Accepted · Rejected · Superseded
- **Decided by** — the human (or team) with authority and accountability for the decision.
- **Drafted by** — who composed the entry text (may be Claude, the human, or both).
- **AI Suggested** — Y / N (did the decision *content* originate with AI?)
- **AI Suggestion Disposition** — Accepted · Modified · Rejected · N/A

**Decision lifecycle.** A decision is *made* now (Status: Proposed → Accepted/Rejected). Its **Outcome** is recorded later, once it's built (Phase 4, Development); its **Lesson Learned** is recorded at Phase 6 (Reflect). Until then those two fields read `— pending`, which is itself useful: it marks a decision as made but not yet validated in practice.

---

## DEC-AISDLC-001 — Canonical DEC-NNN decision schema

> **Amended by DEC-AISDLC-006** — the original `Author` field is superseded by `Decided by` / `Drafted by`. This entry's header below reflects the current convention.

- **Project:** AI-SDLC Framework
- **Status:** Accepted
- **Decided by:** Jorge Valenzuela
- **Drafted by:** Claude
- **Date:** 2026-06-05
- **AI Suggested:** Y
- **AI Suggestion Disposition:** Accepted
- **Context:** Two divergent decision-record field sets existed — Context Document §5 and the Project-Instructions DEC-NNN spec — violating P-002 (decisions are structured data, but the structure had two definitions) and P-017 (consistency across the ecosystem). This entry is recorded in the very schema it defines.
- **Decision:** Adopt a single canonical DEC-NNN schema based on the Project-Instructions version, with three reconciliations: (1) Outcome and Lesson Learned are separate fields; (2) AI disposition is a tri-state (Accepted / Modified / Rejected / N/A) rather than a single boolean; (3) Status includes Superseded with an optional `Supersedes` link. IDs use a per-project prefix (registered: AISDLC, DIS, REVIQO, OOPTW). Outcome and Lesson Learned are expected-empty until implementation / Reflect.
- **Alternatives Considered:** (a) Keep the leaner six-field Context-Doc set — rejected: lacks the metadata that cross-project analytics and automated ingestion need. (b) Merge Outcome into Lesson Learned — rejected: severs the "what happened → what was learned" traceability that Phase 6 / P-001 depend on.
- **Consequences:** Enables cross-project post-mortem analytics and lets decisions feed *forward* into Code Briefs (DEC-AISDLC-002). Costs one extra field per entry and requires updating Context Document §5 to match — an A-hygiene item before the first public tag. *(Authorship convention later amended by DEC-AISDLC-006.)*
- **Outcome:** — pending
- **Lesson Learned:** — pending

---

## DEC-AISDLC-002 — Code Brief as the Phase 2 → Phase 4 handoff

- **Project:** AI-SDLC Framework
- **Status:** Accepted
- **Decided by:** Jorge Valenzuela
- **Drafted by:** Claude
- **Date:** 2026-06-05
- **AI Suggested:** Y
- **AI Suggestion Disposition:** Accepted
- **Context:** P-012 claims software engineering artifacts are precision prompts, but the Phase 2 → Phase 4 handoff mechanism was asserted and never specified — the framework's central differentiator was its one undocumented step.
- **Decision:** Define the **Code Brief** as the handoff unit: a per-iteration *projection* (not a hand-maintained copy) bundling the iteration's scoped requirements, the design-artifact delta, the binding DEC entries, and a Definition of Done — gated on a completed P-013 audit. The brief is the prompt; its invariant is that any natural-language supplement to Claude Code signals an incomplete brief, to be folded back in.
- **Alternatives Considered:** (a) Author the brief from scratch each iteration — rejected: recreates the multi-copy single-source-of-truth problem identified in DEC-AISDLC-001. (b) Hand off the full accumulated design each time — rejected: violates P-015 (design just enough).
- **Consequences:** Operationalizes P-012 and P-013 and closes the Phase 2 ↔ Phase 4 loop — output validates back against the brief, and a mismatch can be an *artifact* bug, not just a code bug. Requires a projection/assembly step and requirement-level IDs. **Open question (v1.0.0):** what tool produces the projection (Claude, a script, or a DIS feature).
- **Outcome:** — pending
- **Lesson Learned:** — pending

---

## DEC-AISDLC-003 — Adopt P-018 "Evaluation Is the Scarce Skill"

- **Project:** AI-SDLC Framework
- **Status:** Accepted
- **Decided by:** Jorge Valenzuela
- **Drafted by:** Claude
- **Date:** 2026-06-05
- **AI Suggested:** Y
- **AI Suggestion Disposition:** Accepted
- **Context:** A thesis-level principle — that critical evaluation, not production, is the scarce human skill in AI-assisted engineering — was latent across P-003, P-014, and LinkedIn Article 1 but had never been extracted.
- **Decision:** Adopt **P-018 — Evaluation Is the Scarce Skill** as a v0.2.0 candidate principle, positioned as the parent thesis that P-003 (restore friction) and P-014 (name the competency to approve) operationalize. Wording gets a revisit before public release; the reflexive structure (approving P-018 is itself an act of P-018) is retained.
- **Alternatives Considered:** (a) Leave it implicit in P-003/P-014 — rejected: the unifying thesis was doing silent work and deserved a name. (b) Fold it into P-014 — rejected: P-014 is phase-local competency, whereas P-018 is the global claim about which competency dominates.
- **Consequences:** Gives the framework its stated reason to exist and supplies a worked example for the still-unwritten principle-graduation criterion (a candidate graduates when it unifies existing principles or resolves a recurring decision). Must be positioned as a parent to avoid reading as redundant with P-003/P-014.
- **Outcome:** — pending
- **Lesson Learned:** — pending

---

## DEC-AISDLC-004 — Branching topology is project-level, not framework-prescribed

- **Project:** AI-SDLC Framework
- **Status:** Accepted
- **Decided by:** Jorge Valenzuela
- **Drafted by:** Claude
- **Date:** 2026-06-05
- **AI Suggested:** N
- **AI Suggestion Disposition:** N/A
- **Context:** The v0.1.0 audit questioned whether gitflow (main/develop/feature) is over-process for solo, build-in-public projects, given P-015.
- **Decision:** Branching topology is a project-level choice, not a framework prescription. The framework requires SemVer, that you branch, and tag-before-transform (P-011) — it does not mandate a specific branch topology. Parked: no active rework of existing branching follows from this; the entry records the boundary.
- **Alternatives Considered:** (a) Mandate gitflow across all projects — rejected: over-process for single-author work. (b) Leave the boundary unspecified — rejected: the framework needs an explicit line between what it mandates and what it leaves to projects.
- **Consequences:** Requires amending P-017's wording, which currently lists "branching strategy (main/develop/feature)" as a cross-project convention; the amendment must split **convention** (shared: SemVer scheme, DEC format, `docs/DECISIONS.md` naming) from **implementation** (project-choice: branch topology). Deferred to v0.2.0 (scope item B.1). Establishes a general framework boundary: AI-SDLC mandates practices and invariants, not implementations.
- **Outcome:** — pending
- **Lesson Learned:** — pending

---

## DEC-AISDLC-005 — "Significant" is the team's call, not a framework-imposed bar

- **Project:** AI-SDLC Framework
- **Status:** Accepted
- **Decided by:** Jorge Valenzuela
- **Drafted by:** Claude
- **Date:** 2026-06-05
- **AI Suggested:** N
- **AI Suggestion Disposition:** N/A
- **Context:** The framework requires capturing "significant" engineering decisions (P-002), but "significant" was never defined — flagged as a gap in the v0.1.0 audit. The risk of leaving it open: either everything gets logged (friction overload) or nothing does (under-logging).
- **Decision:** Significance is determined by the software engineer, manager, or team; AI may flag candidates as significant when it spots them, but AI-SDLC does not impose a universal bar. The framework's job is to make the *discipline* of capturing whatever you judge significant deliberate — not to define a one-size-fits-all rule. AI-SDLC is not an absolute-truth solution for all projects; it helps the practitioner realize which aspects matter while developing with AI-augmented skills.
- **Alternatives Considered:** (a) Define a fixed checklist of "significant" decision types — rejected: presumes one-size-fits-all across projects, which the framework explicitly is not (consistent with DEC-AISDLC-004's "mandate practices, not implementations" boundary). (b) Leave it undefined — rejected: leaves the log's core scope ambiguous.
- **Consequences:** Keeps significance a human judgment (consistent with P-018) while still allowing AI to assist. Trades a crisp universal rule for adaptability across projects and teams. Resolves the audit gap.
- **Outcome:** — pending
- **Lesson Learned:** — pending

---

## DEC-AISDLC-006 — Record who decided, not just who drafted (adopt P-019; amend DEC-001 authorship)

- **Project:** AI-SDLC Framework
- **Status:** Accepted
- **Decided by:** Jorge Valenzuela
- **Drafted by:** Claude
- **Date:** 2026-06-05
- **AI Suggested:** Y
- **AI Suggestion Disposition:** Accepted
- **Supersedes:** AISDLC-001 *(authorship convention only)*
- **Context:** Jorge noticed that every DEC entry recorded "Author: Claude," which read as though Claude autonomously produced the decisions — and, scaled up, the framework itself — erasing the human who initiated, judged, and owned each call. This contradicts P-014 (the human brings accountability) and P-018 (evaluation is the human's value): the framework's own records were crediting only the AI producer. The catch itself was an instance of P-018 — the human evaluating and correcting AI output.
- **Decision:** Adopt **P-019 — Keep the Human Visible** (candidate, v0.2.0): a decision record must name the accountable human, not just the artifact's drafter; provenance is part of the decision. As its first operationalization, amend the DEC-NNN schema (DEC-AISDLC-001) to replace the single `Author` field with `Decided by` (the accountable human/team) and `Drafted by` (who composed the record). `AI Suggested` + `AI Suggestion Disposition` are retained to capture idea origin and the human's response.
- **Alternatives Considered:** (a) Keep `Author` and rely on `AI Suggested` to imply human involvement — rejected: a reader still sees "Author: Claude" and misattributes ownership. (b) Add only `Decided by` and drop drafter tracking — rejected: loses the real, useful record of who did the drafting labor.
- **Consequences:** Every entry now shows human accountability explicitly, protecting the provenance of the framework itself for public release. First use of the `Supersedes` link — which surfaces a likely future need to distinguish *amends* (partial change) from *supersedes* (full replacement); parked as a candidate for v0.2.0 schema work. P-019 clears the principle-graduation criterion (it operationalizes P-014/P-018 and resolves a recurring failure mode).
- **Outcome:** — pending
- **Lesson Learned:** — pending
---

## DEC-AISDLC-007 — License the public release under CC BY 4.0

- **Project:** AI-SDLC Framework
- **Status:** Accepted
- **Decided by:** Jorge Valenzuela
- **Drafted by:** Claude
- **Date:** 2026-06-05
- **AI Suggested:** Y
- **AI Suggestion Disposition:** Accepted
- **Context:** v0.1.0 shipped with the LICENSE marked "pending." The framework is documentation (code lives in its own repos), built in public, with teaching and consulting ambitions — the public release needed explicit legal terms.
- **Decision:** License the AI-SDLC framework under Creative Commons Attribution 4.0 International (CC BY 4.0). Finalized in v0.1.1.
- **Alternatives Considered:** (a) CC BY-SA 4.0 (copyleft) — rejected: no need to force derivatives open, adds adopter friction. (b) A Non-Commercial variant — rejected: would collide with the framework's own consulting/teaching use. (c) A code license (MIT/Apache) — rejected: wrong tool for documentation.
- **Consequences:** Anyone may use, adapt, and commercialize with attribution — maximizing adoption and operationalizing P-019 at the legal layer. Code components remain separately licensed.
- **Outcome:** — pending
- **Lesson Learned:** — pending
---

## DEC-AISDLC-008 — Adopt the principle-graduation criterion

- **Project:** AI-SDLC Framework
- **Status:** Accepted
- **Decided by:** Jorge Valenzuela
- **Drafted by:** Claude
- **Date:** 2026-06-06
- **AI Suggested:** Y
- **AI Suggestion Disposition:** Modified
- **Context:** P-001 says principles are extracted from practice, but there was no stated bar for when a candidate becomes a numbered principle (audit gap; risk of principle inflation as the framework grows in public).
- **Decision:** A candidate is adopted when — drawn from ≥1 real instance (P-001), and not a restatement — it either unifies two or more existing principles under a higher-order truth, or resolves a recurring decision/failure mode. Rewording an unclear principle (maintenance) and splitting a two-job principle (refactoring) are explicitly *not* graduation. Recorded in FRAMEWORK.md §6.
- **Alternatives Considered:** (a) No explicit bar — rejected: invites inflation. (b) Include "explains an existing principle" as a third path — rejected (Jorge): if a new principle is needed to explain an old one, the old one is unclear and should be reworded, not supplemented.
- **Consequences:** Promotion is no longer arbitrary; gives a repeatable test others can apply. Separates graduation from maintenance/refactoring.
- **Outcome:** — pending
- **Lesson Learned:** — pending

---

## DEC-AISDLC-009 — Adopt P-017, P-018, P-019, P-020

- **Project:** AI-SDLC Framework
- **Status:** Accepted
- **Decided by:** Jorge Valenzuela
- **Drafted by:** Claude
- **Date:** 2026-06-06
- **AI Suggested:** Y
- **AI Suggestion Disposition:** Modified
- **Context:** Four candidates carried from the kickoff and this session were ready to promote once the graduation bar was set (DEC-008).
- **Decision:** Promote all four to numbered principles (count 16 → 20). P-017 reworded to split convention from implementation (completing the amendment deferred in DEC-004); P-018 tightened; P-019 settled in DEC-006; P-020 newly adopted. Provenance: P-017/018/019 were AI-surfaced from the audit and reworked under review; **P-020 was originated by Jorge** (the velocity/pacing observation), drafted by Claude.
- **Alternatives Considered:** (a) Keep them as candidates longer — rejected: each clears the bar and is already practiced. (b) Adopt individually across versions — rejected: they form one coherent v0.2.0 set.
- **Consequences:** The human–AI thesis (P-018) and the accountability/pacing discipline (P-019/P-020) are now first-class. P-017's reword obligates the convention-vs-implementation boundary everywhere.
- **Outcome:** — pending
- **Lesson Learned:** — pending

---

## DEC-AISDLC-010 — Reorganize PRINCIPLES.md into thematic sections; generalize four principles

- **Project:** AI-SDLC Framework
- **Status:** Accepted
- **Decided by:** Jorge Valenzuela
- **Drafted by:** Claude
- **Date:** 2026-06-06
- **AI Suggested:** Y
- **AI Suggestion Disposition:** Modified
- **Context:** The flat 20-principle list was hard to read by theme, and four principles carried domain-specific wording narrower than their underlying truth.
- **Decision:** Reorganize PRINCIPLES.md into a chronological index plus 7 thematic sections (numbers = identity, sections = reading aid; cross-cutting principles housed once with cross-references, single source of truth). Generalize-reword P-006, P-009 ("Match the Mechanism to Domain Stability"), P-010 ("invested in"), P-011 ("any significant change"). Maintenance/presentation, not new principles (per DEC-008).
- **Alternatives Considered:** (a) Keep the flat list — rejected: doesn't scale. (b) Duplicate cross-cutting principles per section — rejected: reintroduces the multi-copy drift problem (DEC-001 / P-017).
- **Consequences:** Principles are navigable by theme without losing chronological identity. Rewords broaden applicability; origin notes keep them grounded (P-001).
- **Outcome:** — pending
- **Lesson Learned:** — pending
---

## Glossary

- **DEC-NNN** — a single decision record; NNN is a per-project, zero-padded sequence (e.g., `AISDLC-001`).
- **P-NNN** — an AI-SDLC principle (e.g., P-002, "Decisions Are Data").
- **SemVer** — Semantic Versioning, `MAJOR.MINOR.PATCH`.
- **DIS** — Decision Intelligence System, the companion app that stores and analyzes these decisions.
- **SOLID** — the five object-oriented design principles checked in the P-013 design audit.
- **Code Brief** — the per-iteration bundle handed to Claude Code as the Phase 2 → Phase 4 prompt (see DEC-AISDLC-002).
- **Phases referenced** — Phase 2 (Design), Phase 4 (Development / implementation), Phase 6 (Reflect).

---

*AI-SDLC Framework · `docs/DECISIONS.md` · v0.1.0 · Maintained in DEC-NNN format per DEC-AISDLC-001, as amended by DEC-AISDLC-006*
