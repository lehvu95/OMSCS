# Lesson 4 — Quiz (graded)

> Source: Canvas — CS-7280-O01, OAN (Summer 2026)

Combined view of the six graded quiz questions. See also [[lesson04-quiz-all.pdf]].

---

### Q1 — Multiple choice (1 point)

If the exponent of a power-law degree distribution is $\alpha = 3.25$, which of the following statistical metrics is well-defined (finite)?

- [ ] The kurtosis
- [ ] The skewness
- [ ] The variance
- [ ] The 3rd moment

---

### Q2 — Multiple choice (1 point)

Which of the following is the right name for the following degree distribution plot?

![[img/q02-degree-distribution-plot.png|400]]

- [ ] Linear-linear scale (linear binning)
- [ ] Log-log scale (linear binning)
- [ ] Log-log scale (log-binning)
- [ ] Log-log scale (cumulative)

---

### Q3 — Fill in the Blank (1 point)

The following statements are FALSE or TRUE?

1. Removing a randomly chosen node from a graph with Poisson degree distribution has a larger effect than removing a randomly chosen node from a power-law network ($2<\alpha<3$). — `True` / `False`
2. Under random node removals, the critical threshold for the disintegration of the largest connected component in a Poisson network is higher than the corresponding critical threshold for a power-law network. — `True` / `False`
3. Under higher-degree node targeted attacks, the critical threshold for the disintegration of the largest connected component in a Poisson network is higher than the corresponding critical threshold for a power-law network. — `True` / `False`
4. Removing the same fraction of nodes from a power-law network will have the same effect no matter what the value of the degree exponent $\alpha$. — `True` / `False`

---

### Q4 — Fill in the Blank (1 point)

When your friendship network is disassortative with a power-law distribution, the following statement are FALSE or TRUE?

1. Many low-degree nodes connect to other low-degree nodes. — `True` / `False`
2. The number of connections between the higher-degree nodes is higher than what would be expected based on a $G(n,p)$ model with the same number of nodes and density (assume multi-edges are allowed). — `True` / `False`
3. Many low-degree nodes connect to hubs. — `True` / `False`
4. The number of connections between nodes of degree 1 is less than what would be expected based on a $G(n,p)$ model with the same number of nodes and density. — `True` / `False`

---

### Q5 — Fill in the Blank (1 point)

The following statements about the preferential attachment model are FALSE or TRUE?

1. At each time step, the model adds the one new node in the network. — `True` / `False`
2. The probability that a link of the new node connects to node $i$ depends on the node $i$'s degree. — `True` / `False`
3. A new node is more likely to connect to more recently added nodes. — `True` / `False`
4. The resulting degree distribution has finite mean and variance. — `True` / `False`

---

### Q6 — Multiple choice (1 point)

How many different networks can be generated using the following degree configuration? (Consider self-loops and multi-edges; nodes of the same degree are not interchangeable)

![[img/q06-degree-configuration.png|400]]

- [ ] 4
- [ ] 5
- [ ] 6
- [ ] 7
