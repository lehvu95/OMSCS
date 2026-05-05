# CS6300 Office Hour — February 4, 2026

**Date:** 2026-02-04
**Instructors:** Shin, Paola Spolettini, Will Johnson, Justin

## Course Context

- Week 4 of semester
- A4 (simple Android app) is open; students also watching Object-Oriented Engineering (P2L2) and Android Development (P2L3) lectures
- Gradescope autograder had been experiencing issues for two days prior; resolved by Justin before this session

## Topics Discussed

- **Gradescope hidden tests**: Instructor tests are intentionally hidden — students cannot reproduce them locally because the input parameters are not disclosed. This is by design; gaming the visible output to match expected output without fixing the root cause is not acceptable and points may be deducted if circumvention is detected.
- **Domain-Driven Design (DDD)**: DDD creates a shared ubiquitous language between developers and domain experts, then centers design on that domain model. Most appropriate when domain complexity is the primary source of project complexity (e.g., medical, legally intricate, or safety-critical domains). For simpler domains, DDD is overkill. Flexible adoption — extracting only the relevant elements — is acceptable.
- **When to stop gathering requirements**: Requirements are never complete. "Enough" is determined by: stakeholder sign-off on scope, requirements being testable (defining acceptance criteria), constraints (time, budget, competitors), and the development process. In waterfall, enough means a signed SRS. In agile, enough means sufficient prioritized requirements to begin the first sprint. Requirements continue to evolve and must be tracked against the growing product.

## Q&A

- **Q:** Tests pass locally in IntelliJ but fail hidden Gradescope tests — should the code be changed to match the expected output? → **A:** No. The discrepancy indicates an issue with the code logic. Students should investigate why the program output differs from the expected output, not hard-code to match it. Reproducing the instructor's exact test locally is impossible by design. Gradescope output patterns may hint at what is wrong.
- **Q:** Is domain-driven design practical in real software engineering? → **A:** Yes, in appropriate contexts. When domain complexity is the core challenge (medical, legal, aerospace), DDD is valuable. When domain complexity is low and other concerns dominate, it is overkill. Extracting just the ubiquitous-language principle from DDD is always worthwhile, regardless of whether the full methodology is applied.
- **Q:** How do you know when enough requirements have been gathered before moving to design? → **A:** Enough requirements cover the defined scope, are testable, and have been signed off by key stakeholders. In practice, constraints (time, budget, competition) force the decision. Requirements always evolve; traceability between requirements and the growing product is a critical ongoing challenge.
- **Q:** Where can students find setup instructions for A4 (Android development environment)? → **A:** The Android Development lecture is the primary resource. If the lecture is insufficient, contact the instructional staff via a private Ed post.
- **Q:** The updated A4 instructions say "invalid input text" but Gradescope still expects "invalid message" — which is correct? → **A:** The autograder has been updated; everything is now consistent. Many students have already received full points.

## Announcements

- Gradescope autograder memory issues (last two days) were a bug on Gradescope's side, not an error in student submissions. The issue is resolved; treat remaining test failures as code issues, not autograder issues.
- Paola's talk at a conference (topic: formal requirements, voted on last week) is on February 10. She is presenting on using LLMs to explain formal specifications written in logic.

## Notes

Paola discussed her research on requirements solicitation interviews. Key finding from a 2014–2016 study: errors found during post-hoc requirements analysis are typically not writing errors but elicitation gaps — things that were never collected. Interview quality (preparation, active listening, avoiding bias) is central. LLMs as simulated customers for analyst training is an emerging application, though she believes human analysts remain essential for actual requirements interviews.
