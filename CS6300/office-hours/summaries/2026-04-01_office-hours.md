# CS6300 Office Hour — April 1, 2026

**Date:** 2026-04-01
**Instructors:** Shin, Tara, Will

## Course Context

- First office hour after two-week gap (A6 lockdown week + Georgia Tech spring break)
- Week covering P4L4 (Agile/Shared Development Methods)
- Active assignment: IPD1 (Individual Project Deliverable 1)
- A6 closed during spring break; some accommodations still outstanding — live solution walkthrough deferred to next week
- A6 grades to be released the following Wednesday, concurrent with the solution walkthrough

## Topics Discussed

- **A6 grade release and solution walkthrough:** Solution walkthrough scheduled for April 8. Students with outstanding accommodation submissions are the reason for the one-week delay. A6 grades will be released the same day as the walkthrough. Students must attest to having watched the full solution before submitting any grade appeal; unsupported appeals will not be reviewed.
- **IPD1 — TSL and test case count:** The assignment specifies 50–90 test cases. Excessively long TSL (Test Specification Language) category/property definitions reduce the probability of staying within that bound. The TSL compiler (tool) must be used correctly; circumventing what the tool is supposed to generate (e.g., brute-forcing frames) will result in point deductions.
- **IPD1 — test frame specificity:** Test frames must be specific enough that a reader can unambiguously map a written test case to a generated frame. Generic or overly abstract partitions that cannot be verified against a written test case will receive no credit.
- **IPD1 — test case authorship:** Part 2 test cases must be written manually. AI-assisted test case writing is not permitted in this course. Parsing TSL output to auto-generate test cases (even if technically sophisticated) will receive zero points.
- **IPD1 — importing libraries in test files:** Allowed if Gradescope permits it at submission time. Past creative solutions (e.g., stress-testing or unusual approaches) have occasionally received bonus recognition, but the Gradescope environment has since been hardened.
- **IPD1 — test frame body vs. skeleton:** Test frames (TSL output) are skeletons. Students write test cases (implementations) from those frames. The test cases require a body; test frames are the generated specification artifacts.

## Q&A

- **Q:** Is there an expected line count for the TSL category/property definitions to ensure sufficient coverage? → **A:** No line count requirement. Aim for 50–90 total test cases. Longer definitions risk exceeding that bound.
- **Q:** Is there one correct solution for IPD1? → **A:** No single correct solution, but incorrect solutions exist. The rubric is compositional and assesses multiple angles; deductions are for demonstrably wrong approaches, not for deviation from a single expected answer.
- **Q:** What is an example of using the TSL tool incorrectly? → **A:** Being so generic with partitions that generated test frames cannot be mapped to specific test cases. If a frame could match any test case, it cannot be verified as correct and will receive no points.
- **Q:** Can we import shared library code from IPD2's helper class into the IPD1 test file? → **A:** Allowed if Gradescope accepts the import. Test within the Gradescope environment before final submission.
- **Q:** Must test cases be written manually? Can we auto-generate them from TSL output? → **A:** Test cases must be written manually. Auto-parsing the TSL output to generate test cases — regardless of technical elegance — will receive zero points.
- **Q:** Do test frames require a body? → **A:** Test frames are generated artifacts (skeletons). Test cases (student-authored implementations of those frames) require a body.

## Announcements

- A6 solution walkthrough: April 8 office hour.
- A6 grades release: approximately April 8.
- Grade appeal window for A6: two weeks from grade release; requires prior attestation of having watched the full solution.
