# CS6300 Office Hour — April 8, 2026

**Date:** 2026-04-08
**Instructors:** Paula, Will (Shin absent)

## Course Context

- Week 13
- Primary agenda: A6 solution walkthrough
- IPD2 ongoing

## Topics Discussed

### A6 Solution Walkthrough

The session was dedicated to walking through sample solutions for all four A6 tasks. Solutions presented are one possible correct answer; multiple valid solutions exist.

**Task 1 — Statement coverage does not guarantee fault revelation:**
The sample `unstableMethod1` contains a division-by-zero fault reachable only when `a == 1`. A test suite achieving 100% branch coverage can avoid `a == 1` (e.g., using `a = 0` and `a = -1`), thereby covering all branches without revealing the fault. However, every test suite that does reveal the fault must execute all statements — fault revelation implies 100% statement coverage, but the converse does not hold.

**Task 2 — 100% branch coverage always reveals the fault:**
`unstableMethod2` places the fault (`1 / a` where `a == 0`) inside a branch that is only reachable when `a == 0`. Covering all branches requires one test case with `a == 0` and one with `a ≠ 0`. The test case `a == 0` always reveals the fault. Therefore, every test suite achieving 100% branch coverage will reveal the fault, and revealing the fault requires executing that statement (100% statement coverage).

**Task 3 — Described as impossible (subsumption argument):**
The task asked for a method where 100% statement coverage always reveals the fault, but a test suite achieving 100% path coverage could avoid it. This is impossible: path coverage subsumes branch coverage, which subsumes statement coverage. Any test suite achieving 100% path coverage also achieves 100% statement coverage. If 100% statement coverage always reveals the fault, then so does every test suite achieving 100% path coverage. A proof by contradiction demonstrates this directly from the subsumption hierarchy. Full points required adequately describing this impossibility.

**Task 4 — Applying statement coverage and MCDC to a given method:**
The provided method contains a two-level decision structure: an outer simple condition (`a != b`) and an inner compound condition (`c == 0 && d > 0 || e < 0`).

- Statement coverage (3 test cases): one test case per executable path through the outer condition's two branches plus the inner condition's two outcomes. Example: `(a=b)`, `(a≠b, inner=true)`, `(a≠b, inner=false)`.
- MCDC (minimum 5 test cases): a truth table of 16 rows (4 conditions × 2^4) is built. After collapsing irrelevant rows (when `a == b`, inner conditions are moot), the eligible MCDC pairs for each inner condition are identified:
  - `c == 0`: pair (row 2, row 6)
  - `d > 0`: pair (row 2, row 4)
  - `e < 0`: pairs (3,4), (5,6), (7,8) — any one suffices
  - Rows 2, 4, 6 are required. Adding row 3 covers the `e < 0` pair. Adding any row from 9–16 covers the outer condition's false branch. Minimum: 5 test cases (e.g., rows 2, 3, 4, 6, and one from 9–16).

**Final exercise — Truth table completion and coverage sentence completion:**
A method with conditions on `a` and `b` modifying `x` and `y`, followed by `return (y / x) < 0`:

| a     | b     | Output |
|-------|-------|--------|
| true  | true  | true (negative result) |
| true  | false | error (division by zero) |
| false | true  | error (division by zero) |
| false | false | false |

Sentences completed:
- "A test suite with 100% statement coverage _____ reveals the fault." → **Sometimes** (can select rows {TT, FF} and miss the fault, or {TF, FT} and find it)
- "A test suite with 100% branch coverage _____ reveals the fault." → **Sometimes** (same reasoning — statement coverage ≡ branch coverage here since no empty branches exist)
- "A test suite with 100% path coverage _____ reveals the fault." → **Always** (all four input combinations must be covered; two of them produce the fault)

## Announcements

- A6 grades released concurrent with this session.
- Grade appeals require attestation of having watched this solution in full; appeals submitted without this attestation will be rejected.
- IPD2 is ongoing; students should be starting the second phase of the individual project.
