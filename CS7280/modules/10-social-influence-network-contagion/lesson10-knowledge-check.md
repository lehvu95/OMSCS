# Lesson 10 — Knowledge Check

> Source: Canvas — CS-7280-O01, OAN (Summer 2026)

Ungraded knowledge check. See also [[lesson10-knowledge-check.pdf]].

---

### Q1 — Multiple choice (1 point)

Consider the Linear Threshold model. Given a threshold of 0.6 and given the two nodes which are initially active (green), which nodes will be active after the cascade has taken place?

![[img/kc-q01-network.png|400]]

The answer options are the four network states shown below:

- [ ] Option 1 — ![[img/kc-q01-option-1.png|300]]
- [ ] Option 2 — ![[img/kc-q01-option-2.png|300]]
- [ ] Option 3 — ![[img/kc-q01-option-3.png|300]]
- [ ] Option 4 — ![[img/kc-q01-option-4.png|300]]

---

### Q2 — Multiple choice (1 point)

Under the Deffuant model the parameter $\mu$ represents the convergence parameter. If we wanted the opinions of neighboring nodes (only considering the influence of one pair of neighbors on each other) to flip every iteration what value should we choose for $\mu$?

- [ ] 0.5
- [ ] 0.0
- [ ] 1.0
- [ ] No value exists such that every node's opinion will swap with its neighbor at every iteration.

---

### Q3 — Multiple choice (1 point)

Consider a function $f$, which maps from all possible combinations of items on a restaurant menu to a price in dollars. Some items are bundled in deals which means that when those items are bought together, the price of the bundle is lower than the sum of the individual prices. The price of a bundle is always larger than the price of a subset of that bundle. Based on this information, which of the following is true about this function?

- [ ] The function is neither monotone nor submodular
- [ ] The function is monotone
- [ ] The function is submodular
- [ ] The function is both monotone and submodular

---

### Q4 — Fill in the Blank (1 point)

In the proof for the submodularity of the cascade function in the independent contagion model, we show that when adding a new node $v$ to the initially active set $S$, the increase in the cascade size is greater than (or equal to) the increase in the cascade size when $v$ is added to a superset $T$ of $S$. Which of the following statements are true about the nodes that only get activated after we add $v$ to the initial set of active nodes?

1. Some of them may belong to the original cascade of $S$ — but not to the original cascade of $T$. — `True` / `False`
2. Some of them may belong to neither the initial cascade of $S$, nor the initial cascade of $T$. — `True` / `False`
3. Some of them may belong to the initial cascade of $T$ but not to the initial cascade of $S$. — `True` / `False`
4. Some of them may belong to both the initial cascade of $S$ and of $T$. — `True` / `False`

---

### Q5 — Multiple choice (1 point)

How could you choose the set of initial nodes such that after the cascade all the nodes in a community are activated even if the density of the community is greater than $1-\theta$?

- [ ] Include one member of the community in the initially activated set.
- [ ] Include a fraction of community members greater than $\theta$ in the initially activated set.
- [ ] Include all nodes adjacent to the community in the initially activated set.
- [ ] This is not possible.

---

### Q6 — Fill in the Blank (1 point)

Comparing the linear threshold model and the SIS model we studied in Lesson-9, which of the following statements are true?

1. In the SIS model a node can become susceptible again, but in the linear threshold once a node has become activated it stays that way. — `True` / `False`
2. With a given initially active set of nodes, the linear threshold model is deterministic while the SIS model is probabilistic. — `True` / `False`
3. The linear threshold model can lead to oscillating dynamics while the SIS model cannot. — `True` / `False`
4. Both models may lead to complete cascades/epidemics, activating (or infecting, respectively) all nodes of the network. — `True` / `False`

---

### Q7 — Multiple choice (1 point)

Consider two submodular functions $f(X)$ and $g(X)$. What can be said about the functions $\min(f(X), g(X))$ and $\max(f(X),g(X))$?

- [ ] Both of them are submodular
- [ ] Only $\min(f(X),g(X))$ is submodular
- [ ] Only $\max(f(X),g(X))$ is submodular
- [ ] The two functions may not be submodular
