# Big-O Notation — Topic Summary

> Source: CS-7280-O01, OAN (Summer 2026) — Lesson 2 supplementary readings

## Summary

Big-O notation is the standard mathematical language for describing the asymptotic growth rate of an algorithm's resource consumption — most often running time, but equally applicable to memory. Rather than measuring exact operation counts, which depend on hardware, compiler, and constant factors, Big-O characterizes how cost scales as the input size *n* grows toward infinity. This abstraction lets algorithms be compared independently of implementation details and is the foundation for reasoning about the graph and heap algorithms covered later in Lesson 2.

The notation captures an asymptotic **upper bound**: f(n) = O(g(n)) means that beyond some threshold, f(n) never exceeds a constant multiple of g(n). Lower bounds are expressed with Ω, and tight bounds with Θ. In everyday algorithm analysis the term "Big-O" is used loosely to mean the tight worst-case bound, but the formal distinctions matter when proving optimality (for example, the Ω(n log n) lower bound for comparison sorting).

The key takeaways: constant factors and lower-order terms are dropped; only the dominant term governs asymptotic behavior; and the same algorithm can have different best-, average-, and worst-case complexities. Fluency with the common complexity classes — O(1), O(log n), O(n), O(n log n), O(n²), O(2ⁿ), O(n!) — is a prerequisite for evaluating the trade-offs of the data structures (Fibonacci heaps) and graph algorithms (Kosaraju's SCC, Dijkstra) studied in this lesson.

## Details

### Formal Definition

For functions f and g mapping naturals to non-negative reals:

- **Big-O (upper bound):** f(n) = O(g(n)) if there exist constants c > 0 and n₀ ≥ 0 such that f(n) ≤ c·g(n) for all n ≥ n₀.
- **Big-Omega (lower bound):** f(n) = Ω(g(n)) if f(n) ≥ c·g(n) for all n ≥ n₀.
- **Big-Theta (tight bound):** f(n) = Θ(g(n)) if f(n) = O(g(n)) **and** f(n) = Ω(g(n)).
- **little-o:** f(n) = o(g(n)) if the ratio f(n)/g(n) → 0; a strictly looser upper bound.

### Simplification Rules

1. **Drop constant coefficients:** 3n² + 5 = O(n²).
2. **Keep only the dominant term:** n² + n log n + 100 = O(n²).
3. **Logarithm bases are interchangeable:** logₐn and log_b n differ by a constant factor, so all logarithms are written log n inside Big-O.
4. **Products and compositions:** nested loops multiply (O(n)·O(n) = O(n²)); sequential blocks take the maximum.

### Common Complexity Classes (ascending growth)

| Class | Name | Representative operation |
|---|---|---|
| O(1) | Constant | Array index, hash lookup (amortized) |
| O(log n) | Logarithmic | Binary search, balanced-BST operation |
| O(n) | Linear | Single pass / linear scan |
| O(n log n) | Linearithmic | Merge sort, heap sort, comparison-sort optimum |
| O(n²) | Quadratic | Nested loops, naive all-pairs |
| O(n³) | Cubic | Naive matrix multiply, Floyd–Warshall |
| O(2ⁿ) | Exponential | Subset enumeration, naive recursion |
| O(n!) | Factorial | Permutation enumeration, brute-force TSP |

### Cases of Analysis

- **Worst case** — the maximum cost over all inputs of size n; the default for Big-O.
- **Best case** — the minimum cost; less informative but bounds the lower edge.
- **Average case** — expected cost over a distribution of inputs; e.g., quicksort is O(n²) worst case but Θ(n log n) average.
- **Amortized** — average cost per operation across a worst-case *sequence* of operations. This is the lens through which Fibonacci heaps achieve their bounds — see the [[fibonacci-heap/summary]] topic.

## Examples

- **Linear search** scans an array element by element: best case O(1) (first element), worst case O(n) (absent or last). See [[runtime-and-big-o-notation]].
- **Binary search** halves the search interval each step over a sorted array: O(log n).
- **Bubble/insertion sort** use nested passes: O(n²) worst case; insertion sort is O(n) on already-sorted input (best case).
- **Merge sort** divides and merges: Θ(n log n) in all cases, the comparison-sort optimum. Worked derivations appear in [[big-o-notation-pswads]].
- **Dijkstra with a Fibonacci heap** improves from O(V² ) or O((V+E) log V) to O(E + V log V) precisely because the decrease-key operation becomes O(1) amortized — the motivating payoff connecting this topic to [[fibonacci-heap/summary]] and to the shortest-path material of Lesson 2.

A quick-reference table of operation costs for common containers and algorithms is in [[big-o-cheat-sheet.pdf]]. Reinforcement exercises: [[practice-big-o-exercises.pdf]] and [[practice-time-complexity-gfg.pdf]].

## References

- [[big-o-notation-wikipedia]] — formal definitions of O, Ω, Θ, o, ω.
- [[big-o-notation-pswads]] — *Problem Solving with Algorithms and Data Structures* (C++), Big-O chapter with worked sort analyses.
- [[runtime-and-big-o-notation]] — runtime measurement and intuition.
- [[big-o-cheat-sheet.pdf]] — Big-O complexity cheat sheet (Know Thy Complexities).
- [[big-o-complexity-chart.pdf]] — Big-O complexity chart (condensed two-page bigocheatsheet.com reference).
- Practice: [[practice-big-o-exercises.pdf]], [[practice-time-complexity-gfg.pdf]].
- Related topics: [[fibonacci-heap/summary]], [[kosaraju-algorithm/summary]].
