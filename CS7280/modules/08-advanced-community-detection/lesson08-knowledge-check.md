# Lesson 8 — Knowledge Check

> Source: Canvas — CS-7280-O01, OAN (Summer 2026)

Ungraded knowledge check. See also [[lesson08-knowledge-check.pdf]].

---

### Q1 — Multiple choice (1 point)

Which of the following statements regarding the three approaches to identify communities in a dynamic network is/are TRUE:

- [ ] The evolution of network community structure is done by computing communities separately at each time step.
- [ ] The dual-objective approach leads to the formation of communities with lower modularity at time T+1 than the approach where the communities are separately computed at each time step.
- [ ] The global network is formed by classifying the nodes and links at each time step as local and the links between networks at various time steps as global.
- [ ] The dual-objective approach leads to the formation of the smoothest results as it considers the communities formed at all the previous steps indirectly.

---

### Q2 — Multiple answer (1 point)

Which of the following statements about the CFinder algorithm and random networks is/are FALSE:

- [ ] The critical density threshold increases with the value of $k$ (k for k-cliques).
- [ ] The critical density threshold is the highest density of a random network that makes the formation of k-cliques likely.
- [ ] There are never any k-cliques observed below the critical density threshold.
- [ ] If a network is denser than the critical threshold, CFinder will probably detect many communities even if the network is random.

---

### Q3 — Multiple answer (1 point)

Which of the following statements about the LFR benchmark is/are TRUE:

- [ ] The LFR benchmark generates a network in which all communities have the same size.
- [ ] The only difference between LFR and GN networks is how they model the degree distribution.
- [ ] LFR generates networks in which both the node degrees and community sizes follow power-law distributions.
- [ ] LFR networks can also have overlapping communities.

---

### Q4 — Multiple choice (1 point)

Compute the confusion matrix for the two given partitions and find the missing entries in cells (1,2), (2,1), (2,3), (3,2) in the same order.

![[img/kc-q04-partition-1.png|400]]

![[img/kc-q04-partition-2.png|400]]

- [ ] 0, 1, 2, 0
- [ ] 3, 1, 2, 3
- [ ] 3, 2, 1, 3
- [ ] 0, 2, 1, 0

---

### Q5 — Multiple answer (1 point)

Which of the following statements about Delta-MAPS, as a method to identify spatially-contiguous clusters of grid-cells based on correlations, is/are TRUE:

- [ ] The objective of Delta-MAPS is to identify the maximum number of minimal-size "domains" in the given data.
- [ ] A Delta-MAPS domain can be thought of as a spatially contiguous community in which the nodes represent grid points and the edges represent temporal correlations between the corresponding grid points.
- [ ] The Delta-MAPS algorithm computes one domain in each iteration. In a given iteration, the objective is to compute the largest possible domain subject to the constraint imposed by the parameter $\delta$.
- [ ] Delta-MAPS domains can be overlapping.

---

### Q6 — Multiple choice (1 point)

The left plot shows a network, while the right plot shows one point for each node where the x-coordinate is the Participation Coefficient and the y-coordinate is the Within-Community Degree. We know that the points A, B, C at the right plot correspond to the nodes 0, 9, 10 at the network. Which of the following is the most likely correspondence between points A, B, C and nodes 0, 9, 10?

![[img/kc-q06-network.png|400]]

![[img/kc-q06-scatter.png|450]]

- [ ] A - 10, B - 9, C - 0
- [ ] A - 9, B - 0, C - 10
- [ ] A - 9, B - 10, C - 0
- [ ] A - 0, B - 10, C - 9
