# Lesson 2 — Knowledge Check

> Source: Canvas — CS-7280-O01, OAN (Summer 2026)

Ungraded knowledge check. See also [[lesson02-knowledge-check.pdf]].

---

### Q1 — Multiple choice (1 point)

Which of the following statements about this graph is False?

![[img/kc-q01-graph.png|400]]

- [ ] Sum of all node degrees = 8
- [ ] Number of edges = 8
- [ ] Graph density = 2/9
- [ ] Max number of possible edges = 36

---

### Q2 — Multiple choice (1 point)

How many Strongly Connected Components are there in the following graph? (note that an individual node is, by convention, a strongly connected component)

![[img/kc-q02-scc.png|400]]

- [ ] 3
- [ ] 4
- [ ] 2
- [ ] 1

---

### Q3 — Multiple choice (1 point)

Which of the following statements about this below bipartite graph is False?

![[img/kc-q03-bipartite.png|400]]

- [ ] There is a cycle of length 5
- [ ] The bibliographic coupling of B and D is 1
- [ ] There is a cycle of length 4
- [ ] The weight of the edge AB of the one-mode projection on students is 1

---

### Q4 — Multiple choice (1 point)

Which of the following statements is False?

- [ ] Dijkstra's algorithm can be used for any weighted graph with positive or negative weights to calculate the shortest path from a node to any other node in the graph.
- [ ] BFS can be used for computing all connected components of an undirected graph.
- [ ] BFS can be used for any unweighted graph to calculate the shortest path from a node to any other node in the graph.
- [ ] Tarjan's algorithm can be used to compute the strongly connected components of a directed network.

---

### Q5 — Multiple choice (1 point)

This plot shows a 4-node network with the associated transition matrix. The random walker is initially at node A. What is the stationary distribution for this random walk?

![[img/kc-q05-random-walk.png|400]]

1. $[0.32 \; 0.181 \; 0.282 \; 0.218]^{T}$
2. $[0.181 \; 0.32 \; 0.282 \; 0.218]^{T}$
3. $[0.282 \; 0.218 \; 0.181 \; 0.32]^{T}$
4. $[0.181 \; 0.218 \; 0.282 \; 0.32]^{T}$

- [ ] 1
- [ ] 2
- [ ] 3
- [ ] 4

---

### Q6 — Fill in the Blank (1 point)

Answer true or false for each of the following statements.

1. Dijkstra's shortest path algorithm ($\mathcal{O}(m + n\log n)$) has better running time complexity than the Bellman-Ford algorithm ($\mathcal{O}(m \times n)$) on both dense and sparse non-negative weighted networks. — `True` / `False`
2. Directed acyclic graphs have a unique topological ordering. — `True` / `False`
3. In a social network, checking whether two people are friends requires fewer memory accesses if we use an adjacency matrix instead of an adjacency list. — `True` / `False`
4. Our in and out node strength definition for weighted directed graphs can be also applied to signed graphs where weights can be negative. — `True` / `False`

---

### Q7 — Multiple choice (1 point)

How many walks of length 3 are there between node A and C?

![[img/kc-q07-walks-length-3.png|400]]

- [ ] 3
- [ ] 4
- [ ] 5
- [ ] 6
