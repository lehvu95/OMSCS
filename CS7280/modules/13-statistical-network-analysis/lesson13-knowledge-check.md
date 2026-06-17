# Lesson 13 — Knowledge Check

> Source: Canvas — CS-7280-O01, OAN (Summer 2026)

Ungraded knowledge check. See also [[lesson13-knowledge-check.pdf]].

---

### Q1 — Multiple choice (1 point)

Suppose that you decide to use the capture-recapture method to estimate the size of a network. The size of the first sample (the "marked sample") is 100 nodes, the size of the second sample is 150 nodes, the intersection of the two samples is 100 nodes. What is your estimate of the network size plus/minus one standard deviation?

- [ ] $150 \pm 0$
- [ ] $150 \pm 1$
- [ ] $300 \pm 0$
- [ ] $150 \pm 10$

---

### Q2 — Fill in the Blank (1 point)

This question refers to the inclusion probability of nodes and edges when we use a link-tracing (or traceroute-like) network sampling strategy. Which of the following statements are TRUE?

1. Nodes with high degree are more likely to be included in the sample than nodes with low degree but high betweenness centrality. — `True` / `False`
2. The probability that a node is NOT included in the sample drops exponentially with its betweenness centrality. — `True` / `False`
3. If we swap the set of sources with the set of targets — but maintain their number — we have the same node and edge inclusion probabilities. — `True` / `False`
4. Doubling the number of target nodes will, approximately, double the probability that an edge is sampled. — `True` / `False`

---

### Q3 — Fill in the Blank (1 point)

The following question refers to the Horvitz-Thompson estimator. Which of the following statements is/are TRUE?

1. Suppose we want to estimate the number of nodes with degree=2 using Horvitz-Thompson, and we use incident subgraph sampling. We simply count the number of degree-2 nodes in the sample and then multiply by $N/n$. — `True` / `False`
2. Suppose we want to estimate the number of nodes with degree=2 using Horvitz-Thompson, and we use induced subgraph sampling. We simply count the number of degree-2 nodes in the sample and then multiply by $N/n$. — `True` / `False`
3. Suppose we want to estimate the average degree with traceroute sampling. The Horvitz-Thompson estimator gives lower weight to the nodes with higher betweenness centrality. — `True` / `False`
4. The Horvitz-Thompson estimator can be applied for any given sample of nodes. — `True` / `False`

---

### Q4 — Fill in the Blank (1 point)

This question refers to the link prediction problem and the logistic regression approach we covered in this Lesson. Which of the following statements is/are TRUE?

1. To apply this framework, we need to know certain node pairs that are connected and certain other node pairs that are not connected. — `True` / `False`
2. To apply this framework, we need to have at least one metric defined on node attributes and at least one topological similarity metric for node pairs. — `True` / `False`
3. The logistic regression coefficients are different for each node pair. — `True` / `False`
4. This link prediction framework can be also applied when we do not have any information about node attributes. — `True` / `False`

---

### Q5 — Fill in the Blank (1 point)

This question refers to the inference of association networks. Which of the following statements is/are TRUE?

1. When two genes X and Y are highly correlated, we can infer that X regulates Y. — `True` / `False`
2. Pearson's correlation coefficient mostly captures linear dependencies. — `True` / `False`
3. If the correlation coefficient between two nodes is very high (say 99%), we can be certain that that correlation is statistically significant and the corresponding p-value is very low. — `True` / `False`
4. Suppose we have a network with $m = 10000$ node pairs, and the specified False Discovery Rate $\alpha$ is set to $10^{-6}$. The lowest correlation p-value, across all node pairs, is 0.05. The resulting association network will not have any edges. — `True` / `False`

---

### Q6 — Fill in the Blank (1 point)

In the lesson, we have covered three variations of the topology inference problem. Which of the following is/are example(s) of association network inference?

1. We have measurements of functional activity for regions of interest (ROIs) in the brain and we want to estimate the connectivity between these ROIs. — `True` / `False`
2. We want to develop more efficient package delivery networks for our e-commerce company, but we only have access to information from edge nodes such as the date that the customer receives the package and the date that the order is placed. — `True` / `False`
3. We have two types of nodes, namely, customer and product, and we want to build a bipartite network for product recommendation. Thanks to sales and return data collected over a year, we have partial access to connectivity. However, we want to complete the missing connections of our bipartite model. — `True` / `False`
4. We have a set of scientific papers and we want to build a citation network. — `True` / `False`
