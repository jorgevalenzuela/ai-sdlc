# AI-SDLC — Principles

`PRINCIPLES.md` · AI-SDLC Framework · v0.2.0

These principles were extracted from real project experience, not designed upfront (P-001). Each carries an origin. A candidate is adopted only when it clears the graduation bar (see FRAMEWORK.md). **Numbers are chronological identity (immutable); sections are a reading aid (theme).** A principle lives in full in one section; where it cross-cuts, it's *listed* — not duplicated — in the other.

> Throughout, **significant** is what the engineer, manager, or team judges significant — the framework sets no universal bar (DEC-AISDLC-005).

> **Parked candidates** (not yet adopted; maturing per P-001): **"Credit Follows Origination"** and a possible **tiering of guidance into rules / principles / guidelines** (firm → advisory) — both tracked in `BACKLOG.md`, left for a future version. *(Candidates hold no number until adopted; "Credit" previously carried a provisional P-021 label, now reassigned.)*

---

## Index (chronological)

| # | Principle | Section |
|---|-----------|---------|
| P-001 | Extract, Don't Theorize | Building the framework itself |
| P-002 | Decisions Are Data | Decisions & memory |
| P-003 | AI Removes Engineering Friction — Restore It Deliberately | The human–AI stance |
| P-004 | DECISIONS.md Is the Seed | Decisions & memory |
| P-005 | Validate Interaction Before Optimizing Performance | Design & iteration |
| P-006 | Design Decisions Are Teaching Decisions | Design & iteration |
| P-007 | Name for the Broadest Legitimate Use Case | Product & naming |
| P-008 | Dogfood Your Own Tools First | Building the framework itself |
| P-009 | Match the Mechanism to Domain Stability | Design & iteration |
| P-010 | Stack Preference Is an Engineering Decision | Design & iteration |
| P-011 | Tag Before You Transform | Versioning, consistency & production |
| P-012 | Software Engineering Artifacts Are Precision Prompts | Working through artifacts |
| P-013 | Design Artifacts Are Subjects for Automated Quality Auditing | Working through artifacts |
| P-014 | AI-SDLC Is a Collaborative Competency Framework | The human–AI stance |
| P-015 | Design Just Enough for the Next Iteration | Design & iteration |
| P-016 | Production Guardrails Need Multiple Independent Layers | Versioning, consistency & production |
| P-017 | Consistency Across the Ecosystem | Versioning, consistency & production |
| P-018 | Evaluation Is the Scarce Skill | The human–AI stance |
| P-019 | Keep the Human Visible | Decisions & memory |
| P-020 | Pacing Is the Human's Job | The human–AI stance |
| P-021 | Define by the Whole Boundary | Working through artifacts |

---

## 1. The human–AI stance

*Why the framework exists, and what it asks of the human.*

### P-003 — AI Removes Engineering Friction — Restore It Deliberately
AI coding tools make it too easy to build without thinking like a software engineer. The discipline that normally forces documentation, architecture, and decision-making disappears; it must be restored deliberately through process.
*Origin: Jorge's observation — "I was developing as a developer, not a software engineer."*

### P-014 — AI-SDLC Is a Collaborative Competency Framework
For each phase and task, AI-SDLC defines the human expertise required to critically evaluate, approve, and guide what AI produces. The human is not a passive recipient — they are an informed collaborator who brings domain knowledge, judgment, and accountability to every step.
*Origin: Jorge's insight — "for each stage, there are skills required that the human must have to approve, assess, or accept what AI generates."*

### P-018 — Evaluation Is the Scarce Skill
When AI can produce the artifact, the human's value shifts to judging it. In AI-assisted engineering the scarce, decisive skill is critical evaluation — recognizing, rejecting, and redirecting plausible-but-wrong output — not production. Speed without judgment is just faster mistakes.
*Origin: synthesized from the founding insight ("I was being carried by it") and the convergence of P-003 and P-014, surfaced during the v0.1.0 audit. The parent thesis those two operationalize (DEC-AISDLC-003).*

### P-020 — Pacing Is the Human's Job
AI could produce artifacts faster than a human can absorb and own them. Velocity is not progress: output that outruns the human's understanding is unowned work waiting to fail. Setting the tempo to human comprehension — not AI throughput — is the human's responsibility, and the AI's job is to support that pace, not outrun it.
*Origin: extracted from the v0.2.0 working session — decisions produced faster than they could be internalized; pacing the work to human comprehension was the corrective.*

*Also relevant here (housed elsewhere): → P-012 — Software Engineering Artifacts Are Precision Prompts (Working through artifacts); → P-019 — Keep the Human Visible (Decisions & memory).*

---

## 2. Decisions & memory

*Capturing reasoning so it survives the decision.*

### P-002 — Decisions Are Data
Engineering decisions are not comments — they are structured data. Capture them with context, alternatives, consequences, and lessons. A decision without its reasoning is just a fact; a decision with its reasoning is institutional memory.
*Origin: creation of the DECISIONS.md habit and the Decision Intelligence System.*

### P-004 — DECISIONS.md Is the Seed
Every project starts with a DECISIONS.md, even if empty. It signals intent — this project will be engineered, not just built.
*Origin: the decision to add DECISIONS.md to every project from day one.*

### P-019 — Keep the Human Visible
A decision record must name the accountable human, not just the artifact's drafter. In AI-assisted work it's easy to log only what the AI produced and erase who decided and owned it. Provenance — who raised it, who drafted it, who decided — is part of the decision, and the accountable human stays visible.
*Origin: caught during the v0.1.0 kickoff that every decision record read as authored by the AI, erasing the human who decided; the catch was itself an act of P-018 (DEC-AISDLC-006).*

---

## 3. Working through artifacts

*The method — engineering artifacts are the unit of value when working with AI.*

### P-012 — Software Engineering Artifacts Are Precision Prompts
Anyone can tell AI what they want in plain language. AI-SDLC is about what happens *before* you talk to AI — the engineering thought process that produces precise, artifact-rich inputs. A well-crafted use case, data model, or architecture diagram tells AI exactly what to build, better than any natural-language description.
*Origin: Jorge's insight — "I can tell AI more precisely what I want using software engineering artifacts, not just human language."*

### P-013 — Design Artifacts Are Subjects for Automated Quality Auditing
A class diagram or data model can be evaluated for coupling, cohesion, and SOLID compliance before a single line of code is written. Catch design problems before they become code problems.
*Origin: Jorge's insight about auditing designs against SOLID principles before coding.*

### P-021 — Define by the Whole Boundary
Define a concept by its whole boundary, not just its center: what it *is* and what it *is not*, with examples and non-examples, the things it's confused with, and how to tell. A concept defined only by what it is leaves its edges fuzzy and gets misapplied — understanding, and good design, live at the boundary.
*Origin: Jorge's teaching and definition methodology, named while defining the framework's own terms — accountability, responsibility, and the voided artifact.*

---

## 4. Design & iteration

*How you design — just enough, in the right order, fit to the domain.*

### P-005 — Validate Interaction Before Optimizing Performance
Get the concept right first, then make it fast. A fast response to a bad UX is still bad UX. Isolate UI/interaction concerns from infrastructure concerns.
*Origin: Phase 1 local LLM before Phase 2 cloud API migration.*

### P-006 — Design Decisions Are Teaching Decisions
Every interface teaches the user how to think about the system, so every design decision is, implicitly, a teaching decision. A blank text box teaches that knowledge is accessed by knowing what to ask; a concept map teaches that knowledge is a connected system.
*Origin: 3D concept map as primary interaction model.*

### P-009 — Match the Mechanism to Domain Stability
Fit the dynamism of your solution to how fast the domain actually changes. For a stable, curated domain, a static or simpler mechanism is a feature, not a limitation — don't build for volatility the domain doesn't have. *(First seen in retrieval: a static knowledge base beats live RAG when the knowledge rarely changes.)*
*Origin: OOP Tutor Web — static vs live knowledge base decision.*

### P-010 — Stack Preference Is an Engineering Decision
A developer invested in their stack writes better, more intentional code — engagement with the tools shows up in the work. Don't default to what's familiar; choose deliberately. Stack preference is a legitimate engineering input, not a footnote.
*Origin: Decision Intelligence System — Node.js over Python.*

### P-015 — Design Just Enough for the Next Iteration
Over-designing ahead of implementation produces artifacts that change before they are used. Design enough to build the next iteration confidently — no more. Let the design grow with the system.
*Origin: Jorge's decision to follow iterative development with "design just enough."*

---

## 5. Versioning, consistency & production

*Discipline that protects the system as it ships, scales, and runs.*

### P-011 — Tag Before You Transform
Before any significant change, tag the current stable state. A working version is a valuable asset — protect it before you change it, so there's always a known-good point to return to.
*Origin: Git branching strategy adopted before the 3D concept map redesign.*

### P-016 — Production Guardrails Need Multiple Independent Layers
A single guardrail is insufficient for production AI. Effective guardrails require independent layers: meta-question detection, intent classification, and output validation. Each layer catches what the others miss.
*Origin: discovered testing OOP Tutor guardrails — novel bypass patterns required separate solutions.*

### P-017 — Consistency Across the Ecosystem
A convention adopted in one project applies to all of them, and once adopted it binds. But the framework standardizes only **conventions** — shared formats, what gets captured, where it lives — not **implementations**, the project's own choice of *how* to meet them. The test: standardize a choice when cross-project uniformity creates value (comparable records, tooling that works everywhere); leave it to the project when uniformity buys nothing. *(E.g. SemVer and DEC-NNN are conventions; branch topology and stack are implementations — P-010.)*
*Origin: noticed during the v0.1.0 kickoff that the framework itself was on calendar versioning while every project under it used SemVer; sharpened when branch topology forced the convention-vs-implementation distinction (DEC-AISDLC-004).*

---

## 6. Product & naming

*How you frame and position the work.*

### P-007 — Name for the Broadest Legitimate Use Case
Name tools and projects for their broadest legitimate use, not their first use case. A tool named after one course number signals a one-off; a tool named after a concept signals a product.
*Origin: renaming CIS501 AI Tutor → OOP Tutor Web.*

---

## 7. Building the framework itself

*Meta — how you build a methodology or tooling, and validate it.*

> *Contextual principles — these apply when you're building tools, a methodology, or shaping a project, and don't all bind every project (e.g., P-008 assumes you build tools you can use).*

### P-001 — Extract, Don't Theorize
Build the framework by doing — extract principles from real projects. A framework built in isolation produces academic artifacts; a framework extracted from practice produces usable tools.
*Origin: the decision to build AI-SDLC from existing projects rather than designing it upfront.*

### P-008 — Dogfood Your Own Tools First
If you build a tool that enforces good practices, use it yourself first. The first project to fully use the Decision Intelligence System is the Decision Intelligence System itself.
*Origin: the self-documentation principle of the DIS project.*

---

*AI-SDLC Framework · `PRINCIPLES.md` · v0.2.0 · 21 principles, 7 sections · numbers chronological, sections thematic*
