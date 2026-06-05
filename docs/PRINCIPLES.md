# AI-SDLC — Principles

`docs/PRINCIPLES.md` · AI-SDLC Framework · v0.1.0

These principles were extracted from real project experience, not designed upfront (P-001). Each carries an origin — the concrete decision or observation it came from.

> Candidate principles under consideration for v0.2.0 (P-017 Consistency Across the Ecosystem, P-018 Evaluation Is the Scarce Skill, P-019 Keep the Human Visible) are recorded as decisions in [`DECISIONS.md`](./DECISIONS.md) and are **not yet adopted** here.

---

### P-001 — Extract, Don't Theorize
Build the framework by doing — extract principles from real projects. A framework built in isolation produces academic artifacts; a framework extracted from practice produces usable tools.
*Origin: the decision to build AI-SDLC from existing projects rather than designing it upfront.*

### P-002 — Decisions Are Data
Engineering decisions are not comments — they are structured data. Capture them with context, alternatives, consequences, and lessons. A decision without its reasoning is just a fact; a decision with its reasoning is institutional memory.
*Origin: creation of the DECISIONS.md habit and the Decision Intelligence System.*

### P-003 — AI Removes Engineering Friction — Restore It Deliberately
AI coding tools make it too easy to build without thinking like a software engineer. The discipline that normally forces documentation, architecture, and decision-making disappears; it must be restored deliberately through process.
*Origin: Jorge's observation — "I was developing as a developer, not a software engineer."*

### P-004 — DECISIONS.md Is the Seed
Every project starts with a DECISIONS.md, even if empty. It signals intent — this project will be engineered, not just built.
*Origin: the decision to add DECISIONS.md to every project from day one.*

### P-005 — Validate Interaction Before Optimizing Performance
Get the concept right first, then make it fast. A fast response to a bad UX is still bad UX. Isolate UI/interaction concerns from infrastructure concerns.
*Origin: Phase 1 local LLM before Phase 2 cloud API migration.*

### P-006 — Design Decisions Are Teaching Decisions
In educational software, every UI/UX decision is also a pedagogical decision. A blank text box teaches that knowledge is accessed by knowing what to ask; a concept map teaches that knowledge is a connected system.
*Origin: 3D concept map as primary interaction model.*

### P-007 — Name for the Broadest Legitimate Use Case
Name tools and projects for their broadest legitimate use, not their first use case. A tool named after one course number signals a one-off; a tool named after a concept signals a product.
*Origin: renaming CIS501 AI Tutor → OOP Tutor Web.*

### P-008 — Dogfood Your Own Tools First
If you build a tool that enforces good practices, use it yourself first. The first project to fully use the Decision Intelligence System is the Decision Intelligence System itself.
*Origin: the self-documentation principle of the DIS project.*

### P-009 — Match Retrieval Strategy to Domain Stability
Not all RAG systems need live retrieval. For stable, curated domains, a static knowledge base is a feature, not a limitation. Match the retrieval strategy to the rate of change of the domain.
*Origin: OOP Tutor Web — static vs live knowledge base decision.*

### P-010 — Stack Preference Is an Engineering Decision
A developer who enjoys their stack writes better, more intentional code. Don't default to what's familiar — choose deliberately. Stack preference matters.
*Origin: Decision Intelligence System — Node.js over Python.*

### P-011 — Tag Before You Transform
Every significant UI or architectural change starts with a version tag on the current stable state. A working version is a valuable asset — protect it before changing it.
*Origin: Git branching strategy adopted before the 3D concept map redesign.*

### P-012 — Software Engineering Artifacts Are Precision Prompts
Anyone can tell AI what they want in plain language. AI-SDLC is about what happens *before* you talk to AI — the engineering thought process that produces precise, artifact-rich inputs. A well-crafted use case, data model, or architecture diagram tells AI exactly what to build, better than any natural-language description.
*Origin: Jorge's insight — "I can tell AI more precisely what I want using software engineering artifacts, not just human language."*

### P-013 — Design Artifacts Are Subjects for Automated Quality Auditing
A class diagram or data model can be evaluated for coupling, cohesion, and SOLID compliance before a single line of code is written. Catch design problems before they become code problems.
*Origin: Jorge's insight about auditing designs against SOLID principles before coding.*

### P-014 — AI-SDLC Is a Collaborative Competency Framework
For each phase and task, AI-SDLC defines the human expertise required to critically evaluate, approve, and guide what AI produces. The human is not a passive recipient — they are an informed collaborator who brings domain knowledge, judgment, and accountability to every step.
*Origin: Jorge's insight — "for each stage, there are skills required that the human must have to approve, assess, or accept what AI generates."*

### P-015 — Design Just Enough for the Next Iteration
Over-designing ahead of implementation produces artifacts that change before they are used. Design enough to build the next iteration confidently — no more. Let the design grow with the system.
*Origin: Jorge's decision to follow iterative development with "design just enough."*

### P-016 — Production Guardrails Need Multiple Independent Layers
A single guardrail is insufficient for production AI. Effective guardrails require independent layers: meta-question detection, intent classification, and output validation. Each layer catches what the others miss.
*Origin: discovered testing OOP Tutor guardrails — novel bypass patterns required separate solutions.*

---

*AI-SDLC Framework · `docs/PRINCIPLES.md` · v0.1.0 · 16 principles extracted from practice (P-001)*
