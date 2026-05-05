# CS6300 Office Hour — February 26, 2026

**Date:** 2026-02-26
**Instructors:** Shin, Paula

## Course Context

- Week 7
- Lectures assigned: P3L4 (Unified Software Process), P4L1 (Testing: General Concepts)
- Two submissions due this week:
  - GPD2: one team member submits on Canvas; all members responsible for verification
  - Individual Design Assessment: each student submits on Gradescope (peer evaluation of GPD1 teammates)

## Topics Discussed

- **GPD2 deliverable expectations:** Paula emphasized using the provided templates as guides, reading each section's description carefully, and asking whether a reader unfamiliar with the project would understand the artifact. Balance between completeness and conciseness is key; overly verbose documents are as problematic as under-specified ones.
- **Unified Software Process phase naming in project plan:** Teams may use either UP phase names (inception, elaboration, etc.) or traditional software development activity names. What matters is that descriptions, entrance criteria, and exit criteria are complete and coherent.
- **Persistence in the Android app:** If persistence is specified in the assignment instructions, it is required. If not, it is an implementation decision. Caution: many teams lose points because SQLite (local persistence) is not initialized correctly on first install; the TA tests by installing fresh and opening the app.
- **Supported device assumptions:** The assignment specifies a target device (Pixel 6 or Pixel 8). Assumptions and constraints should be documented in one of the GPD templates; the relevant section is included in the template.
- **Team roles in GPD3/GPD4:** Roles are defined for coordination and accountability, not strict task isolation. Full-stack collaboration is expected and encouraged.
- **Research discussion — automatic debugging:** Paula discussed a paper by the course creator and Chris Parnin on evaluating automatic debugging tools. Key insight: a tool that localizes a bug to a large code region is not useful in practice, because developers do not read code that way. Usefulness must be defined relative to developer workflows, not just precision metrics.
- **Research discussion — formal verification and AI:** Extended discussion on model checking, theorem proving, and whether AI can lower the barrier to formal methods adoption. Consensus: AI may make formal methods more accessible, but cannot substitute human judgment for critical-path systems. Studies show automated natural-language-to-formal-specification translation reaches at most 50% correctness unassisted and 80% with human-in-the-loop, which is insufficient for safety-critical contexts.
- **AI-generated code maintainability:** Discussed a study (attributed to an ICSE paper) on what agents do well and poorly in development teams. Maintainability of AI-generated code is a known weakness; implications for long-term codebases are unresolved.

## Q&A

- **Q:** Are there sample deliverables or more detailed direction for GPD2? → **A:** Templates are provided and contain examples for project plan, use case model, and test plan. Use the template structure as a checklist. The deliverable descriptions themselves contain guidance; read them carefully as each section serves a specific purpose.
- **Q:** Should project plan activities use UP nomenclature or generic software development activities? → **A:** Either is acceptable. Entrance criteria, exit criteria, and descriptions must be complete and self-explanatory regardless of naming convention.
- **Q:** Does the app need to implement data persistence? → **A:** Follow the assignment instructions. If persistence is required, implement it. Ensure SQLite or any local store is initialized correctly on first launch — this is a common source of grading failures.
- **Q:** Can we assume one supported device? Where do we document this? → **A:** Yes. Document device assumptions and constraints in the designated section of the relevant GPD template.
- **Q:** Are team roles expected to represent strict ownership, or can members collaborate across areas? → **A:** Roles define accountability and coordination. Collaborative, cross-functional work is expected and reflects industry norms.
