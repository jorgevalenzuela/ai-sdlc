# AI-SDLC — Framework

`docs/FRAMEWORK.md` · AI-SDLC Framework · v0.2.0

## 1. What is AI-SDLC?

AI-SDLC is a structured software development lifecycle for AI-assisted projects. It combines traditional software-engineering discipline with AI as a high-productivity collaborator, ensuring that speed of development does not come at the cost of engineering quality.

> The core insight: **AI removes engineering friction. AI-SDLC restores it deliberately.** (P-003)

The framework was developed through practice on real projects, not designed upfront in theory (P-001).

## 2. The lifecycle: phases and their elements

AI-SDLC's lifecycle is a **Template Method**: a fixed, ordered skeleton of phases — the canonical sequence — within which each iteration fills in, right-sizes, or voids the work.

**Two levels.**

- **Phases — the coupled core.** Ordered, numbered, and *always traversed*. Intentionally interdependent (like Scrum's events): a phase is never silently skipped, because dropping one quietly weakens the whole loop. A phase number denotes canonical order — nothing more.
- **Elements — within a phase.** The steps and activities AI-SDLC defines inside each phase. Elements are where an iteration flexes: an iteration may **void** an element it doesn't need.

**Phase vs. element — the rule.** The distinction is *coupling to the loop*, not importance (every part matters). A **phase** is a guaranteed checkpoint: every iteration traverses it. You cannot declare a phase "not needed" — you arrive at it and decide, even if that decision is to void all its elements. The stop is non-negotiable; only the work inside is conditional. An **element** is a conditional step inside a phase: an iteration may find it unneeded and void it (considered → justified → approved → recorded).

*Test for any candidate activity:* must every iteration stop here as a checkpoint? → phase. Or is this a step an iteration might find unnecessary and void? → element.

**Voiding is a state, not a skip.** A void moves through *considered → justified → approved → recorded*. It is never a silent omission — it produces a **voided artifact**. This keeps the friction (P-003) and makes the decision data (P-002).

**The floor of a phase.** A phase can have *every* element voided and still produce, at minimum, a justified voided artifact. That record is what makes the phase exist; a phase is never absent. (This structurally blocks the "we run Scrum but quietly dropped retros" degradation.)

**Voided artifact — template** (defined by its whole boundary, P-021):

| Field | Captures |
|---|---|
| What was voided | the element(s) set aside this iteration |
| Why | the positive reason it isn't needed |
| Cost of *not* voiding | what would break or be wasted if done anyway (the negative space) |
| Approved by | the accountable human (never the AI) |

### Canonical phase sequence

| # | Phase | Elements |
|---|-------|----------|
| 0 | Vision | — |
| 1 | Requirements | elicit → diagram → validate → prioritize · output = admitted scope (§4) |
| 2 | Design | diagram → validate → **approval gate** |
| 3 | Project Configuration | setup (once) · reconfiguration (on new req/design) |
| 4 | Development | implement · unit testing |
| 5 | Testing | integration · system |
| 6 | Release | regression · QA |
| 7 | Deployment / DevOps | build & package · pipeline run · environment promotion · **deployment approval gate** · post-deploy verification · observability · rollback readiness |
| 8 | Reflect | post-mortem review · decision outcomes reviewed (Phase 4/8 fields filled) · principles graduated (P-001, §6) · framework updates |

*Phase 3 configures the **project** (repo, structure); Phase 7 configures and operates the **runtime** (environments, pipelines, monitoring). Unit testing (Phase 4) is co-located with implementation; integration/system testing stands alone (Phase 5). Reflect (Phase 8) is the iteration's post-mortem — the checkpoint where principles graduate; it is never voided to nothing without a recorded reason.*

## 3. Iteration: a path through the skeleton

An **iteration** traverses the phase skeleton in order and right-sizes the work inside each phase:

- It **runs every phase** — the spine is always present; it never skips phases.
- Inside each phase, it **voids the elements** it doesn't need — each void justified, approved, recorded.
- "Happens once" is gone. A phase is *traversed every iteration and right-sized*. Vision and Project Configuration are typically heavy in iteration 1 and largely voided afterward (revisited on a pivot or structural change) — but nothing freezes them.
- An iteration's scope is the set of requirements admitted in Phase 1 (§4), chosen by the accountable human/team.

Scope and the SemVer bump track the iteration type:

| Iteration | Phase 1 scope | Phase 2 scope | SemVer |
|-----------|---------------|---------------|--------|
| I1 — core feature | Requirements for this iteration only | Design just enough for I1 | MINOR bump (e.g. 1.0.0 → 1.1.0) |
| I2 — next feature | Requirements for this iteration only | Add to design — not full redesign | MINOR bump (e.g. 1.1.0 → 1.2.0) |
| Bug fix | Not required | Not required | PATCH bump (e.g. 1.1.0 → 1.1.1) |
| Breaking change | Full re-elicitation | Significant redesign | MAJOR bump (e.g. 1.x.x → 2.0.0) |

## 4. Requirements

A requirement faces two separate questions: *is it well-formed?* (quality) and *does it belong in the contract?* (admission). AI-SDLC keeps them apart.

### Quality criteria — is it well-formed?

Every requirement must satisfy all of the following. Flag any violation before proceeding to design.

| Criterion | Definition | Test question |
|-----------|------------|---------------|
| Unique | No two requirements say the same thing | Does any other requirement cover this? |
| Testable | Verifiable through testing or inspection | How would I prove this works? |
| Traceable | Origin and path are explicit — the requirement traces back to the use case or need it came from, and carries a stable ID that later artifacts (design, code, tests) can trace forward to | What's its origin, and can I follow its trace both ways — back to the need, forward to what implements it? |
| Unambiguous | Only one interpretation possible | Could two developers implement this differently? |
| Feasible | Achievable within project constraints | Can we build this in this iteration? |
| Complete | No missing details that block implementation | Does a developer have everything needed? |

These mirror IEEE 29148, with one deliberate exception: AI-SDLC does **not** treat "Necessary" as a quality attribute. Because the SRS is a contract of what will be built, necessity is checked at admission (below), not as a per-requirement quality property.

### Admission — does it enter the SRS?

The SRS is a contract: everything in it is committed to be built this iteration. A candidate requirement is *admitted* when it —

1. **traces to a real stakeholder need** (genuine need, not gold-plating),
2. **is committed to be built this iteration** (P-015 — just enough), and
3. **passes the quality criteria above.**

A real need you're not building yet isn't rejected — it's a backlog item, admitted in a later iteration when you commit to it. In-SRS ⇒ being built; the contract stays honest. *(This mirrors the principle-graduation bar in §6 — a gate before something enters the canon.)*

## 5. Decision management

Every significant engineering decision is captured as structured data (P-002), using the Decision Intelligence System (DIS) or at minimum a `docs/DECISIONS.md` file (P-004). What counts as "significant" is the engineer's, manager's, or team's call; AI may flag candidates (see `DECISIONS.md`, DEC-AISDLC-005).

The canonical record format is **DEC-NNN** (defined in [`DECISIONS.md`](./DECISIONS.md), DEC-AISDLC-001):

`ID` · `Project` · `Status` (Proposed/Accepted/Rejected/Deferred/Superseded) · `Decided by` · `Drafted by` · `Date` · `Context` · `Decision` · `Alternatives Considered` · `Consequences` · `AI Suggested` (Y/N) · `AI Suggestion Disposition` (Accepted/Modified/Rejected/N/A) · `Outcome` *(filled at Phase 4)* · `Lesson Learned` *(filled at Phase 8)* · `Supersedes` *(optional)* · `Amends` *(optional)*

IDs use a per-project prefix (e.g. `AISDLC-001`, `DIS-001`).

## 6. How principles are adopted

Principles are not declared; they graduate from practice (P-001). Phase 8 (Reflect) is where lessons from real decisions become candidate principles — but a candidate has to clear a bar before it gets a number.

A candidate is **adopted** when — drawn from at least one real instance in practice, and not a restatement of an existing principle — it either:

- **unifies** two or more existing principles under a higher-order truth they're both instances of (a parent thesis — e.g. P-018 over P-003 + P-014), or
- **resolves a recurring decision or failure mode**.

Two moves are deliberately *not* graduation: if a principle reads unclearly, **reword it** (maintenance); if it's doing two jobs, **split it** (refactoring). Both change an existing principle rather than minting a new one.

Once adopted, a principle takes the next chronological number (immutable identity) and slots into whatever thematic section fits (see [`PRINCIPLES.md`](./PRINCIPLES.md)).

## 7. Branching & SemVer

| Branch | Purpose |
|--------|---------|
| main | Production-ready code only. Never commit directly; only receives merges from develop. |
| develop | Integration branch. Feature branches merge here first; tested before merging to main. |
| feature/[name] | One branch per iteration or feature. Created from develop; merged back when complete. |

Release sequence per iteration: merge feature → develop → push → merge develop → main → push → tag SemVer → push tag → return to develop.

> **Note (P-017):** branch *topology* is a project-level choice, not a framework prescription — the framework requires SemVer, that you branch, and tag-before-transform (P-011), but not a specific topology (DEC-AISDLC-004). P-017 now splits shared **conventions** from project **implementations**, and topology is an implementation. The table above is a default *example*, not a mandate.

| Version | When | Example |
|---------|------|---------|
| MAJOR | Breaking change | 1.x.x → 2.0.0 — complete UI redesign, API incompatibility |
| MINOR | New feature, backwards compatible | 1.0.0 → 1.1.0 — new exam engine added |
| PATCH | Bug fix, no new features | 1.1.0 → 1.1.1 — fixed login redirect bug |

---

## 8. Glossary

*Each term is defined by its whole boundary (P-021). Example / non-example rows are optional and may be filled in as the framework matures.*

### Accountability *(AI-SDLC ecosystem)*

- **Is** — a named *human* owns a decision or outcome and can be asked to answer for it.
- **Is not** — blame; and never the AI's. Claude can produce and propose, but cannot be accountable.
- **Confused with** — responsibility.
- **How to tell** — can you name the one human who answers for this? If not, there's no accountability, only activity.
- *Example (opt.)* — Jorge approving a DEC entry. *Non-example* — "the model decided it" (no named human → no accountability).

### Responsibility *(AI-SDLC ecosystem)*

- **Is** — the duty to *do / produce* the work. Can be held by a human **or** the AI.
- **Is not** — answering for the outcome (that's accountability).
- **Confused with** — accountability.
- **In AI-SDLC** — Claude is *responsible* for drafting and producing; the approving human is *accountable*. This is the `Drafted by` / `Decided by` split (P-019).
- *Example (opt.)* — Claude drafting the Phase 7 spec. *Non-example* — Claude "owning" whether it ships (it can't).

### Voided artifact

- **Is** — the justified, approved record produced when an element is voided; the trace of a deliberate non-action.
- **Is not** — a silent skip or a gap.
- **How to tell** — every voided element carries the four-field record (what · why · cost of not voiding · approved by). No record → it's an omission (a defect), not a void.
- *Example (opt.)* — voiding integration tests on a config-only iteration, with justification. *Non-example* — simply not testing and saying nothing.

---

*AI-SDLC Framework · `docs/FRAMEWORK.md` · v0.2.0 · Principles in [`PRINCIPLES.md`](./PRINCIPLES.md) · Decisions in [`DECISIONS.md`](./DECISIONS.md)*
