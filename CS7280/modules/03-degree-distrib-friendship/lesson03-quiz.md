# Lesson 3 — Quiz (graded)

> Source: Canvas — CS-7280-O01, OAN (Summer 2026)

Combined view of the eight graded quiz questions. See also [[lesson03-quiz-all.pdf]]. The answer key is in [[lesson03-quiz-answers]].

---

### Q1 — Multiple choice (1 point)

What would be the average degree and the standard deviation of the degree distribution for a graph with 8 nodes whose empirical degree distribution is as shown below?

![[img/q01-degree-distribution.png|500]]

- [ ] $\bar{k} = 5/4$, $\sigma = \frac{\sqrt{27}}{4}$
- [ ] $\bar{k} = 5/4$, $\sigma = \frac{\sqrt{23}}{4}$
- [ ] $\bar{k} = 7/4$, $\sigma = \frac{\sqrt{23}}{4}$
- [ ] $\bar{k} = 7/4$, $\sigma = \frac{\sqrt{27}}{4}$

---

### Q2 — Multiple choice (1 point)

What is the expected degree of a node's neighbor in the graph below?

![[img/q02-neighbor-degree-graph.png|400]]

- [ ] 2.0
- [ ] 2.4
- [ ] 2.5
- [ ] 2.6

---

### Q3 — Multiple choice (1 point)

Which of the following graphs would be the most extreme instance of the Friendship Paradox?

![[img/q03-friendship-paradox-panels.png|600]]

- [ ] 1
- [ ] 2
- [ ] 3
- [ ] 4

---

### Q4 — Multiple choice (1 point)

If you can only vaccinate 2 people, who would you immunize based on the following network of contacts?

![[img/q04-vaccination-network.png|450]]

- [ ] (A,E)
- [ ] (B,F)
- [ ] Two randomly selected individuals
- [ ] (F,D)

---

### Q5 — Multiple choice (1 point)

Consider the $G(n,p)$ model of random graphs with $n=1000$ nodes. What is the minimum value of $p$ so that the largest connected component is expected to include all nodes? Round off your answer to three decimal places.

- [ ] 0.006
- [ ] 0.007
- [ ] 0.008
- [ ] 0.009

---

### Q6 — Multiple choice (1 point)

Which of the following statements is true for the **in-degree distribution** of a random DIRECTED network? The number of nodes is $n$ and the probability that any node $x$ connects to any node $y$ (other than $x$) is $p$.

1. $p_k = \binom{n}{k} p^k (1-p)^{n-k}$
2. $p_k = \frac{1}{2}\binom{n-1}{k} p^k (1-p)^{n-k-1}$
3. $p_k = \binom{n-1}{k} p^k (1-p)^{n-k-1}$
4. $p_k = 2\binom{n-1}{k} p^k (1-p)^{n-k-1}$

- [ ] 1
- [ ] 2
- [ ] 3
- [ ] 4

---

### Q7 — Multiple choice (1 point)

What is the average neighbor degree for node $v$?

![[img/q07-node-v-network.png|400]]

- [ ] 4
- [ ] 3
- [ ] 2
- [ ] 1

---

### Q8 — Multiple choice (1 point)

Which one of the following statements is **True**?

- [ ] We expect that a $G(n, p)$ network is connected if the average node degree is 1.
- [ ] The friendship paradox can be observed in any network
- [ ] We use Poisson distribution instead of Binomial distribution to model degree distribution of the $G(n,p)$ networks because it is more accurate for small $p$ values.
- [ ] Effects of the Friendship Paradox is more significant if $\frac{\overline{k^2}}{\bar{k}} \gg \bar{k}$
