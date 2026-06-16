# Lesson 6 — Knowledge Check

> Source: Canvas — CS-7280-O01, OAN (Summer 2026)

Ungraded knowledge check. See also [[lesson06-knowledge-check.pdf]].

---

### Q1 — Multiple choice (1 point)

Five friends are planning to go on a vacation to Europe, the starting city is New York and the ending city of the trip is Atlanta. Each one of them independently comes up with a plan to visit cities in sequential order in Europe. All the cities these 5 people include in their plan are considered to be the nodes and the sequence to be represented by directed edges in a network. If the starting city New York is considered to be the source node and the ending city, Atlanta is considered to be the target node then each of these five plans is nothing but source-target paths.

Which centrality metric is the best to decide the most desirable city that they all wish to visit?

- [ ] Closeness Centrality
- [ ] Harmonic Centrality
- [ ] Path Centrality
- [ ] Betweenness Centrality

---

### Q2 — Multiple choice (1 point)

Suppose there is a network representing an underwater cave system with several entrances and exits. The network is directed and has no cycles in the intermediate nodes (the network is a DAG) which represent pockets of air in the cave system. All of the edges are weighted equally. Suppose we want to know the minimum number of intermediate nodes needed to cover all possible paths from entrances to exits. Which of the following would be the best approach that could be used to find a core-group useful for answering this question?

- [ ] Tau-Core
- [ ] K-Core Decomposition
- [ ] Min-Cut (for nodes)
- [ ] Rich Club Membership

---

### Q3 — Multiple choice (1 point)

Consider a directed acyclic network showing how information is passed from the leaders of a terrorist group to the "foot soldiers". Our national security agency wants to intercept most of these messages but they cannot afford to tap all messages. They would like to select only a few individuals in the network and tap those. Which of the following metrics would you recommend to use for selecting those individuals?

- [ ] Degree centrality
- [ ] tau-core
- [ ] Closeness centrality
- [ ] Rich Club Membership

---

### Q4 — Multiple choice (1 point)

Identify the tau-core set in the following graph for $\tau = 0.875$ (hint: there are 16 total paths, $14/16 = 0.875$)

![[img/kc-q04-tau-core.png|400]]

- [ ] G, F, H
- [ ] G, F, E
- [ ] I, J
- [ ] G, I, J

---

### Q5 — Fill in the Blank (1 point)

Which of the following statements about PageRank centrality is/are True:

1. The PageRank centrality of a node is computed on the basis of all outgoing edges from the node. — `True` / `False`
2. The PageRank centrality of a node is computed on the basis of all incoming edges to the node. — `True` / `False`
3. The main idea behind PageRank centrality is that if a node has $k$ outgoing connections then its centrality should be split among these neighbors. — `True` / `False`
4. The main idea behind PageRank centrality is that if a node has $k$ incoming connections then its centrality should be split among these neighbors. — `True` / `False`

---

### Q6 — Fill in the Blank (1 point)

In the following figure, we show an undirected network. What does the three-node network (A,B,C) correspond to?

![[img/kc-q06-rich-club-network.png|400]]

1. $k$-core of this network with a $k=2$. — `True` / `False`
2. $k$-core of this network with a $k=3$. — `True` / `False`
3. Rich club set with $k=1$ (the average "rich-club coefficient" is $\phi(k) = 0.58 \pm 0.12$ among 10,000 random networks). — `True` / `False`
4. Rich club set with $k=2$ (the average "rich-club coefficient" is $\phi(k) = 0.76 \pm 0.20$ among 10,000 random networks). — `True` / `False`
