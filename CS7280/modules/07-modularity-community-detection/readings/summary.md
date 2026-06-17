# Lesson 7 Recommended Reading — Topic Summary

> Source: CS-7280-O01, OAN (Summer 2026) — Lesson 7 supplementary reading

## Summary

The single Lesson 7 reading is the paper behind the lecture's "Optimized Greedy Algorithm" for modularity maximization. The lesson develops greedy modularity maximization conceptually — repeatedly merging the pair of communities whose union yields the largest increase in modularity $Q$ — and notes that, with the right data structures, the cost can be driven down to $O(N \log^2 N)$. This reading is the source of that result: it presents the fast-greedy ("CNM") algorithm that made modularity-based community detection tractable on very large networks for the first time.

The unifying point is that modularity maximization is NP-hard in general, so practical community detection rests on efficient heuristics. The fast-greedy algorithm is the canonical such heuristic: it sacrifices the global optimum but, by exploiting the sparsity of real networks and maintaining the modularity-gain values in efficient data structures (a max-heap of community-pair $\Delta Q$ values plus balanced binary trees), it scales to networks with millions of nodes. This is exactly why the lesson singles it out when moving from the abstract greedy idea to something usable at scale.

The key takeaway: the near-linear running time on sparse networks is what turns greedy modularity maximization from a textbook idea into a method that can be run on web-, citation-, and collaboration-scale graphs, at the cost of returning a good — not provably optimal — partition.

## Details

- **Finding community structure in very large networks.** [[finding-community-structure-very-large-networks.pdf]] (Aaron Clauset, M. E. J. Newman, Cristopher Moore, *Physical Review E* 70, 066111, 2004) gives the fast-greedy agglomerative algorithm for maximizing modularity $Q$. Starting from each vertex in its own community, it repeatedly merges the community pair that produces the largest increase (or smallest decrease) $\Delta Q$ in modularity, recording the partition at every step and finally reporting the one with the highest $Q$. The contribution is algorithmic: rather than recomputing $Q$ from scratch, the method stores the sparse matrix of $\Delta Q_{ij}$ values, a max-heap of the largest $\Delta Q$ per row, and uses balanced trees so that each merge updates only the affected entries. On a sparse network with $n$ vertices and $m$ edges this yields a running time of $O(m\, d \log n)$, where $d$ is the depth of the resulting dendrogram — close to linear, $O(n \log^2 n)$, for the sparse, hierarchical networks typical in practice. It is the predecessor-improving successor to Newman's 2003 "Fast algorithm for detecting community structure in networks" and is the standard reference for the lesson's optimized greedy modularity maximization.

## Examples

- **Collaboration and web-scale graphs** — the paper demonstrates the algorithm on networks far larger than earlier spectral or betweenness-based methods could handle (hundreds of thousands to millions of vertices), including a purchasing/recommendation network, recovering community structure in time that grows roughly linearly with network size.
- **Dendrogram and the $Q$ curve** — because the algorithm records the partition after every merge, plotting modularity $Q$ against the number of merges produces a curve whose peak identifies the partition reported as the community structure, mirroring the lesson's description of selecting the cut with maximum $Q$.

## References

- [[finding-community-structure-very-large-networks.pdf]] — A. Clauset, M. E. J. Newman, C. Moore, *Finding Community Structure in Very Large Networks*, Physical Review E 70, 066111, 2004 — <https://doi.org/10.1103/PhysRevE.70.066111> (arXiv: `cond-mat/0408187`).
