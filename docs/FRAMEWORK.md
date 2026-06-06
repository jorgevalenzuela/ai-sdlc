# AI-SDLC — Framework

`docs/FRAMEWORK.md` · AI-SDLC Framework · v0.2.0

## 1. What is AI-SDLC?

AI-SDLC is a structured software development lifecycle for AI-assisted projects. It combines traditional software-engineering discipline with AI as a high-productivity collaborator, ensuring that speed of development does not come at the cost of engineering quality.

> The core insight: **AI removes engineering friction. AI-SDLC restores it deliberately.** (P-003)

The framework was developed through practice on real projects, not designed upfront in theory (P-001).

## 2. The 7 phases

| # | Phase | When | Outputs | AI role |
|---|-------|------|---------|---------|
| 0 | Vision | Once — whole project | Vision statement, stakeholders, project name, problem definition | Co-author vision, suggest stakeholders |
| 1 | Requirements | Per iteration | Use cases, functional + non-functional requirements, constraints | Elicit requirements via structured interview, check quality criteria |
| 2 | Design | Per iteration — just enough | Class diagram, DB schema, API contract, UI wireframes, architecture | Generate and audit design artifacts against SOLID, normalization, coupling |
| 3 | Project Setup | Once — whole project | Repo, branching strategy, DECISIONS.md, README | Scaffold structure, generate initial docs |
| 4 | Development | Per iteration | Working code, passing builds, documented decisions | Translate design artifacts to code — artifacts *are* the prompts |
| 5 | Release | Per iteration | Merged branch, SemVer tag, updated README, exported DECISIONS.md | Generate commit messages, update documentation |
| 6 | Reflect | Per iteration | Completed decision entries, new principles extracted, framework updates | Analyze decisions, suggest principles, identify patterns |

## 3. Iterative development model

Phases 0 and 3 happen once. Phases 1, 2, 4, 5, 6 repeat every iteration. Design just enough for the next iteration — no more (P-015).

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

`ID` · `Project` · `Status` (Proposed/Accepted/Rejected/Superseded) · `Decided by` · `Drafted by` · `Date` · `Context` · `Decision` · `Alternatives Considered` · `Consequences` · `AI Suggested` (Y/N) · `AI Suggestion Disposition` (Accepted/Modified/Rejected/N/A) · `Outcome` *(filled at Phase 4)* · `Lesson Learned` *(filled at Phase 6)* · `Supersedes` *(optional)*

IDs use a per-project prefix (e.g. `AISDLC-001`, `DIS-001`).

## 6. How principles are adopted

Principles are not declared; they graduate from practice (P-001). Phase 6 (Reflect) is where lessons from real decisions become candidate principles — but a candidate has to clear a bar before it gets a number.

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

*AI-SDLC Framework · `docs/FRAMEWORK.md` · v0.2.0 · Principles in [`PRINCIPLES.md`](./PRINCIPLES.md) · Decisions in [`DECISIONS.md`](./DECISIONS.md)*
