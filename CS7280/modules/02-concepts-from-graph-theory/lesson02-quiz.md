# Lesson 2 — Quiz (graded)

> Source: Canvas — CS-7280-O01, OAN (Summer 2026)

Combined view of the seven graded quiz questions. See also [[lesson02-quiz-all.pdf]]. The answer key is in [[lesson02-quiz-answers]].

---

### Q1 — Multiple choice (1 point)

Which of the following statements about this graph is **False**?

![[img/q01-walk-cycle-graph.png|400]]

- [ ] The sequence 'BDCB' is a walk and a cycle
- [ ] The sequence 'BCDBA' is a path
- [ ] The sequence 'GEF' is a walk
- [ ] The sequence 'FEG' is a path

---

### Q2 — Multiple choice (1 point)

Find the max flow of the following network.

![[img/q02-max-flow-network.png|400]]

- [ ] 20
- [ ] 23
- [ ] 21
- [ ] 24

---

### Q3 — Multiple choice (1 point)

Which of the following node sequences is **NOT** a topological order of this graph?

![[img/q03-topological-order-graph.png|300]]

- [ ] AGBEDCF
- [ ] GABEDCF
- [ ] ABGEDCF
- [ ] ABEDGCF

---

### Q4 — Multiple choice (1 point)

Which of the following statements is **False**?

- [ ] In a flow network, the amount of maximum flow is always equal to capacity of the minimum cut.
- [ ] An undirected graph is connected if and only if there exist(s) one or more paths from any node to any other node
- [ ] A graph is a DAG if and only if there is a topological ordering of its nodes
- [ ] Two nodes, $s$ and $t$, belong in the same strongly connected component if and only if there is a path from $s$ to $t$

---

### Q5 — Multiple choice (1 point)

Which of the following expressions is equal to the number of walks of length 2 between two distinct nodes $i,j$ in a graph with adjacency matrix $A$? You can assume that there are no self-loops.

1. $A_{i,j}$ (where $i \neq j$)
2. $\sum_{k=1}^{n} A_{i,k} A^{T}_{k,j}$ (where $i \neq j$, $j \neq k$, and $k \neq i$)
3. $\sum_{k=1}^{n} A_{i,k} A_{k,j}$ (where $i \neq j$, $j \neq k$, and $k \neq i$)
4. None of the above

- [ ] 1
- [ ] 2
- [ ] 3
- [ ] 4

---

### Q6 — Multiple choice (1 point)

Which of the following statements about an Adjacency matrix and Adjacency list is **True**?

- [ ] The size of the Adjacency matrix is $n \times m$ where $n$ is the number of vertices and $m$ is the number of edges
- [ ] Most elements of the adjacency matrix of a dense graph are zeros.
- [ ] The number of adjacency list's entries is $n$ plus the sum of all node degrees.
- [ ] A graph is sparse only if the number of edges remains constant as the network grows.

---

### Q7 — Multiple choice (1 point)

Consider the directed graph shown in the figure below. There are multiple shortest paths between vertices $S$ and $T$. Which one will be reported by Dijkstra's shortest path algorithm? Assume that, in any iteration, the shortest path to a vertex $v$ is updated only when a strictly shorter path to $v$ is discovered.

![[img/q07-dijkstra-graph.png|500]]

- [ ] SDT
- [ ] SBDT
- [ ] SACDT
- [ ] SACET
