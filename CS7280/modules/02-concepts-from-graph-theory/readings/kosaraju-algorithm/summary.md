# Kosaraju's Algorithm and Strongly Connected Components — Topic Summary

> Source: CS-7280-O01, OAN (Summer 2026) — Lesson 2 supplementary readings

## Summary

A **strongly connected component (SCC)** of a directed graph is a maximal set of vertices in which every vertex is reachable from every other vertex. SCCs partition a directed graph, and contracting each SCC to a single node yields the **condensation graph**, which is always a directed acyclic graph (DAG). This decomposition is foundational to the directed-graph material in Lesson 2: it underlies reachability, 2-SAT, dependency resolution, and the connectivity structure (weakly vs. strongly connected components) covered in the lecture.

**Kosaraju's algorithm** computes all SCCs in linear time, O(V + E), using two depth-first searches and the central insight that a graph and its **transpose** (all edges reversed) have exactly the same SCCs. The first DFS orders vertices by decreasing finish time; the second DFS, run on the transpose in that order, peels off one SCC per DFS tree. Its conceptual simplicity — two passes of plain DFS plus an edge reversal — makes it the easiest SCC algorithm to reason about and implement correctly.

The key takeaways: SCCs and the condensation DAG are the right abstraction for "mutual reachability" in directed graphs; Kosaraju, Tarjan, and the path-based algorithm all run in O(V + E) but differ in passes and constants (Tarjan needs a single DFS with a stack and low-link values, and is usually faster in practice); and the condensation DAG enables DAG techniques such as topological order and DAG dynamic programming.

## Details

### Definitions

- **Strongly connected:** for every ordered pair (u, v), there is a directed path u → v and a directed path v → u.
- **SCC:** a maximal strongly connected subgraph.
- **Condensation graph:** contract each SCC to one supernode; the result is a DAG whose topological order is meaningful for downstream computation.

### Kosaraju's Algorithm

1. **First pass.** Run DFS over the original graph G, pushing each vertex onto a stack when its DFS call finishes (post-order / decreasing finish time).
2. **Transpose.** Build Gᵀ by reversing every edge.
3. **Second pass.** Pop vertices off the stack in order; for each not-yet-visited vertex, run DFS on Gᵀ. Each DFS tree produced is exactly one SCC.

Correctness rests on the finish-time ordering: the vertex with the latest finish time lies in a "source" SCC of the condensation DAG, and transposing makes that SCC a sink so its DFS cannot escape into other components. Complexity is O(V + E): two linear DFS passes plus a linear transpose. Full proof in [[kosaraju-algorithm-wikipedia]] and [[scc-condensation-cp-algorithms]].

### Tarjan's Algorithm (single-pass alternative)

Tarjan's algorithm finds SCCs in a **single** DFS by maintaining, for each vertex, a discovery index and a **low-link** value (the smallest index reachable from its subtree via the DFS stack). Vertices are pushed onto an auxiliary stack as they are visited; when a vertex's low-link equals its own index, it is the root of an SCC and the stack is popped down to it. One pass, no transpose — typically faster than Kosaraju in practice. See [[tarjan-scc-gfg]].

### Condensation and Applications

Contracting SCCs yields a DAG suitable for topological sorting and DAG DP. Canonical applications: **2-SAT** (a formula is satisfiable iff no variable shares an SCC with its negation), dependency/build ordering, deadlock detection, and analysis of web/citation graphs. The condensation construction is detailed in [[scc-condensation-cp-algorithms]].

## Examples

- **Worked SCC decomposition** with both Kosaraju and Tarjan: [[scc-gfg]] and [[kosaraju-scc]].
- **Condensation to a DAG** and the source/sink SCC argument: [[scc-condensation-cp-algorithms]].

### Practice Problems

Reachability and condensation-DAG modeling:
- [[practice-cses-planets-and-kingdoms.pdf]] — direct SCC labeling.
- [[practice-cses-flight-routes-check.pdf]] — single-SCC (strong connectivity) check.
- [[practice-cses-coin-collector.pdf]] — condensation + DAG DP for maximum path weight.
- [[practice-codeforces-427c.pdf]], [[practice-codeforces-e.pdf]] — SCC counting / costs.
- SPOJ set: [[practice-spoj-capcity.pdf]], [[practice-spoj-tfriends.pdf]], [[practice-spoj-gooda.pdf]], [[practice-spoj-adapanel.pdf]], [[practice-spoj-lego.pdf]].
- GeeksforGeeks judge problem: [[practice-scc-tarjan-gfg.pdf]]; general set: [[practice-coding-problem.pdf]].
- UVA archive problems: [[practice-uva-p247.pdf]], [[practice-uva-p11324.pdf]], [[practice-uva-p11709.pdf]], [[practice-uva-p11770.pdf]], [[practice-uva-p11838.pdf]], [[practice-uva-p12645.pdf]], [[practice-uva-p12745.pdf]], [[practice-uva-p12926.pdf]], [[practice-uva-p13057.pdf]].

## References

- [[kosaraju-algorithm-wikipedia]] — Kosaraju's algorithm, correctness proof.
- [[scc-condensation-cp-algorithms]] — SCC and condensation graph (CP-Algorithms).
- [[scc-gfg]] — strongly connected components overview (GeeksforGeeks).
- [[kosaraju-scc]] — Kosaraju walkthrough for SCC.
- [[tarjan-scc-gfg]] — Tarjan's single-pass algorithm.
- Related topics: [[big-o/summary]], [[fibonacci-heap/summary]].
