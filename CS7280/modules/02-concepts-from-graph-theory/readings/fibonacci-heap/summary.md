# Fibonacci Heap — Topic Summary

> Source: CS-7280-O01, OAN (Summer 2026) — Lesson 2 supplementary readings

## Summary

A Fibonacci heap is a priority-queue data structure that achieves the best known amortized bounds for the operations that dominate graph algorithms such as Dijkstra's shortest path and Prim's minimum spanning tree. Introduced by Michael Fredman and Robert Tarjan in 1984, it supports insert, find-min, union, and decrease-key in O(1) amortized time, and delete-min (extract-min) and delete in O(log n) amortized time. The decisive advantage over a binary heap is the O(1) amortized **decrease-key**: Dijkstra performs one decrease-key per edge, so a Fibonacci heap lowers Dijkstra's complexity from O((V+E) log V) to O(E + V log V).

The structure trades the rigid shape of a binary heap for a loose collection of heap-ordered trees and a policy of **lazy work**. Costly restructuring is deferred until an extract-min forces a consolidation, and the amortized analysis (via a potential function) shows the deferred cost averages out cheaply over any sequence of operations. The name reflects the analysis: the minimum possible size of a node of degree *k* grows as the (k+2)-th Fibonacci number, which bounds the maximum degree at O(log n).

The key takeaways: Fibonacci heaps are the theoretical optimum for decrease-key-heavy workloads; their guarantees are *amortized*, not worst-case per operation; and their large constant factors and pointer overhead mean that in practice simpler structures (binary or pairing heaps) often win on real inputs. The structure is studied here as the priority queue that makes the Lesson 2 shortest-path bounds tight.

## Details

### Structure

- A Fibonacci heap is a collection of **heap-ordered trees** (each child's key ≥ its parent's key) whose roots are linked in a circular doubly linked **root list**.
- A pointer to the **minimum node** gives O(1) find-min.
- Each node stores: key, degree (number of children), a child pointer, a circular doubly linked sibling list, a parent pointer, and a boolean **mark** bit.
- Trees are not kept in any balanced shape; restructuring is deferred ("lazy").

### Core Operations

| Operation | Amortized cost | Mechanism |
|---|---|---|
| insert | O(1) | Add a single-node tree to the root list; update min pointer |
| find-min | O(1) | Return the min pointer |
| union (merge) | O(1) | Concatenate two root lists; update min pointer |
| extract-min | O(log n) | Remove min, promote its children to roots, **consolidate** |
| decrease-key | O(1) | Cut node, move to root list, **cascading cut** up the tree |
| delete | O(log n) | decrease-key to −∞, then extract-min |

### Consolidation (during extract-min)

After removing the minimum and promoting its children to the root list, roots of equal degree are repeatedly linked (the larger-key root becomes a child of the smaller) until all roots have distinct degrees. This is what bounds the maximum degree at O(log n) and pays off the deferred work — detailed in [[fibonacci-heap-deletion-gfg]].

### Decrease-Key and Cascading Cuts

When a key decreases below its parent's, the node is **cut** from its parent and moved to the root list (its mark is cleared). If the parent was already marked (it had previously lost a child), the parent is also cut — a **cascading cut** that propagates upward. The mark bit ensures no node loses more than two children before itself being cut, which keeps trees "bushy" enough to preserve the Fibonacci-number degree bound.

### Amortized Analysis

The bounds are proven with the potential method, Φ = (number of trees) + 2·(number of marked nodes). Cheap operations (insert, decrease-key) raise the potential slightly; extract-min's expensive consolidation is paid for by the potential released. The minimum number of descendants of a degree-k node is F(k+2) ≥ φ^k (φ the golden ratio), giving maximum degree D(n) = O(log n). The original proof is in [[Fredman-Tarjan-Fibonacci-Heaps.pdf]].

## Examples

- **Dijkstra's shortest path:** V extract-min operations (O(V log V)) plus up to E decrease-key operations (O(E) amortized) yields O(E + V log V) — strictly better than the binary-heap O((V+E) log V) on dense graphs. This is the direct link to the shortest-path material of Lesson 2.
- **Prim's MST:** same decrease-key-per-edge pattern, same improvement.
- **Insertion and union** build the lazy root list without restructuring; see [[fibonacci-heap-insertion-union-gfg]].
- A runnable implementation is provided in [[FibonacciHeap-master.zip]].
- Practice with the underlying Fibonacci-number recurrence: [[practice-sum-of-fibonacci-gfg.pdf]].

## References

- [[fibonacci-heap-wikipedia]] — structure, operations, and amortized analysis.
- [[fibonacci-heap-introduction-gfg]] — gentle introduction and motivation.
- [[fibonacci-heap-insertion-union-gfg]] — insert and union operations.
- [[fibonacci-heap-deletion-gfg]] — extract-min, decrease-key, delete, consolidation.
- [[Fredman-Tarjan-Fibonacci-Heaps.pdf]] — Fredman & Tarjan (1984), the original paper.
- [[Small09.pdf]] — supplementary academic reference on heap analysis.
- [[fibonacci-heaps-slides.pdf]] — lecture slide deck on Fibonacci heaps (structure, operations, amortized analysis).
- [[FibonacciHeap-master.zip]] — reference implementation.
- Practice: [[practice-sum-of-fibonacci-gfg.pdf]].
- Related topics: [[big-o/summary]] (amortized analysis), [[kosaraju-algorithm/summary]].
