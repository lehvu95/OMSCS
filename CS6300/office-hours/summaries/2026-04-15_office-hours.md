# CS6300 Office Hour — April 15, 2026

**Date:** 2026-04-15
**Instructors:** Shin, Paula

## Course Context

- Week 14 of 16 (spring semester)
- No new lecture content this week
- Active assignment: IPD3
- IPD1 closed; IPD2 autograded

## Topics Discussed

- **MCDC test case count — follow-up from April 8:** Paula revisited the A6 MCDC task. Rows 2, 4, and 6 of the truth table are required (no alternatives exist for covering the `c == 0` and `d > 0` conditions). To also cover `e < 0`, at least one additional pair must be selected (e.g., rows 3+4, or 5+6). One test case from rows 9–16 covers the outer condition's false branch. Minimum total: 5 test cases. Choosing 6 is still valid but not minimal; exceeding 5 is acceptable for full credit unless the bonus (minimum) is being pursued.
- **MCDC loophole via code refactoring:** If the compound condition `c == 0 && d > 0 || e < 0` is extracted into a single Boolean variable `T`, the control flow graph collapses to a single condition, reducing the required MCDC test cases. This is a known limitation of MCDC's dependency on the control flow representation rather than the logical semantics of the code. However, A6 instructs students to apply MCDC to the given code without modification; refactoring is not permitted.
- **`a != b` as a single condition:** A student asked why `a` and `b` are not treated as separate MCDC conditions. Paula clarified: `a != b` is one atomic condition whose truth value depends on the combination of `a` and `b`, but `a` and `b` are treated as input variables, not independent conditions. Only one test case is needed to make `a != b` true and one to make it false.
- **Compliance training format (tangential):** Shin and Paula briefly discussed institutional security compliance training, noting the growing inclusion of AI phishing content in recent training cycles.

## Q&A

- **Q:** For MCDC on A6 Task 4, is it possible to achieve full coverage with fewer than five test cases by "refactoring the table"? → **A:** No. The assignment requires applying MCDC to the given code without modification. Flattening a compound condition into a combined truth table does not comply with the MCDC definition as applied to the original control flow graph. Fewer than five test cases cannot satisfy the minimum coverage requirements under the given structure.
- **Q:** Now that IPD1 has closed, can we get insight into what exactly should have been covered? → **A:** IPD1 rubric details cannot be disclosed while IPD2 is still open, as subsequent deliverables build on IPD1. Details will be released once the full individual project is complete. IPD2 is autograded; Gradescope results indicate coverage percentage immediately upon submission.
- **Q:** For IPD3, can we reuse helper functions from the IPD2 test class? → **A:** Yes. Code written by the student may always be reused. Code provided as course template material (e.g., file-open utilities) may also be reused without citation.
- **Q:** Were students expected to achieve full IPD2 test scenario coverage with the test cases from IPD1? → **A:** No. IPD1 and IPD2 are assessed independently. A stronger IPD1 submission provides a better starting point for IPD2, but IPD1 scoring is not contingent on IPD2 coverage outcomes.

## Announcements

- Students who are behind on lecture viewing should complete all lectures to avoid participation point deductions.
- Office hour chat is read-only for students due to institutional privacy regulations; questions must be posted to the designated discussion board thread.
