# Lesson 5 — Quiz (graded)

> Source: Canvas — CS-7280-O01, OAN (Summer 2026)

Combined view of the six graded quiz questions. See also [[lesson05-quiz-all.pdf]].

---

### Q1 — Multiple choice (1 point)

What is the transitivity of the network below?

![[img/q01-transitivity-network.png|200]]

- [ ] 9/14
- [ ] 5/8
- [ ] 11/15
- [ ] 23/30

---

### Q2 — Fill in the Blank (1 point)

Select the right choice for following statements regarding the CPL and efficiency of an undirected and connected network.

1. The average shortest-path length is less than or equal to the diameter — `True` / `False`
2. As the CPL increases, the related efficiency decreases — `True` / `False`
3. The efficiency of a complete graph with 10 nodes is 1 — `True` / `False`
4. As the CPL increases, the diameter increases. — `True` / `False`

---

### Q3 — Multiple choice (1 point)

Which of the following statements about the Watts-Strogatz model is True?

- [ ] As the rewiring probability $p$ increases, the CPL decreases linearly
- [ ] In the WS model, to have strong clustering (similar to a lattice network with the same average degree), the rewiring probability should be more than about 10%
- [ ] As the rewiring probability $p$ increases, the diameter decreases logarithmically
- [ ] If the rewiring probability of the WS model is sufficiently large, the network diameter will be at the same level with the corresponding $G(n,p)$ network

---

### Q4 — Multiple choice (1 point)

Which of the following statements about the Preferential Attachment (PA) is True?

- [ ] The CPL of the PA model (degree exponent = 3) has the same asymptotic growth with the CPL of $G(n,p)$
- [ ] The diameter of the PA model increases slower than the diameter of $G(n,p)$
- [ ] The average clustering coefficient of the PA model decreases faster compared to the $G(n,p)$ model
- [ ] The average clustering coefficient of the PA model is the same with the $G(n,p)$ model

---

### Q5 — Multiple choice (1 point)

Which of the following statements about network motifs is True?

- [ ] The directed configuration model can generate random directed networks preserving the in-degree and out-degree of each node
- [ ] The method we discussed in the lecture uses random sampling without replacement to compute statistically significant motifs
- [ ] Suppose that $m(G)$ is the number of "mutual out" instances in the given graph $G$, and $m(G_r)$ is the random variable that counts the number of "mutual out" instances in a random graph. If the probability that $m(G_r)$ is larger than $m(G)$ is 99%, the "mutual in" motif is more common in $G$ than expected by chance with a 99% statistical confidence

---

### Q6 — Multiple choice (1 point)

First, calculate the CPL and the diameter for the following network. How large is the difference: diameter minus CPL? Round to 2 decimal places.

![[img/q06-cpl-diameter-network.png|500]]

- [ ] 0.95
- [ ] 0.70
- [ ] 1.05
- [ ] 0.85
