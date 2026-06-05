# AI-SDLC Framework

*An AI-augmented software development lifecycle — built in public.*

**Status:** v0.1.0 · working draft · build-in-public
**Author:** Jorge Valenzuela, Ph.D. — Computer Science Professor & Software Engineer
*Framework authored from real project practice (P-001). Documentation drafted with AI assistance (Claude), decided and owned by the author (P-019).*

> Repository name is a working placeholder (`ai-sdlc`) pending the P-007 naming decision.

---

## What it is

AI-SDLC is a structured software development lifecycle for AI-assisted projects. It exists to answer a problem its author ran into directly: AI coding tools make it too easy to build *without* thinking like a software engineer.

> The core insight: **AI removes engineering friction. AI-SDLC restores it deliberately.** (P-003)

It defines 7 phases (Vision → Requirements → Design → Setup → Development → Release → Reflect), 16 principles extracted from practice, requirements quality criteria, and a decision-tracking format — all designed so that what you hand to AI is a precise engineering artifact, not a vague description (P-012).

## Repository contents

- [`docs/FRAMEWORK.md`](./docs/FRAMEWORK.md) — the 7 phases, iterative model, quality criteria, decision management, branching & SemVer
- [`docs/PRINCIPLES.md`](./docs/PRINCIPLES.md) — the 16 principles, each with its origin
- [`docs/DECISIONS.md`](./docs/DECISIONS.md) — the framework's own decision log (DEC-NNN format)
- [`CHANGELOG.md`](./CHANGELOG.md) — release history, tied to SemVer

## Using it with Claude

Upload `docs/FRAMEWORK.md` and `docs/PRINCIPLES.md` at the start of a new project, then:

> "I'm starting a new project following the AI-SDLC framework. Let's begin with Phase 0 — Vision."

Claude then follows the phases, applies the principles, elicits requirements against the quality criteria, tracks decisions, and guides each iteration. Useful prompts: *"Review these requirements against the quality criteria"*, *"Audit this class diagram for SOLID compliance (P-013)"*, *"Document this decision in DEC-NNN format (P-002)."*

## Status & versioning

This is a working draft, evolving in public. Versioning follows SemVer; the target is **v1.0.0** as the first stable public release. Candidate principles and in-flight decisions (e.g. P-017/18/19) are recorded in [`docs/DECISIONS.md`](./docs/DECISIONS.md) and promoted into the framework at tagged releases — the *edge* version carries candidates, the *released* version is what's meant for adoption.

## License

Licensed under **CC BY 4.0** (Creative Commons Attribution 4.0 International) — see [`LICENSE`](./LICENSE). Use, adapt, and share with attribution. Code components in the wider ecosystem carry their own code licenses.
