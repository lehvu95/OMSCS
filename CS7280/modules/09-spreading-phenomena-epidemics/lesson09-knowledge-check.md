# Lesson 9 — Knowledge Check

> Source: Canvas — CS-7280-O01, OAN (Summer 2026)

Ungraded knowledge check. See also [[lesson09-knowledge-check.pdf]].

---

### Q1 — Multiple choice (1 point)

What is the purpose of the "Exposed" (E) compartmental state in the SEIR model?

- [ ] To represent individuals who have been exposed but not become infected
- [ ] To represent individuals who are infected but not symptomatic
- [ ] To represent individuals who are infected but not contagious
- [ ] To create a distinction between individuals who will eventually become infected versus those that will not

---

### Q2 — Multiple choice (1 point)

Given an average number of neighbors $\bar{k}$, an infection rate $\beta$, a recovery rate $\mu$ and an initial infection percentage $i_0$, determine the rate of change for the infection percentage per infinitesimal time period $dt$.

- [ ] $\frac{di(t)}{dt} = \bar{k}\beta i(t)(1-i(t)) - \mu i(t)$
- [ ] $\frac{di(t)}{dt} = \bar{k}\beta i(t)(1-i(t))\mu i(t)$
- [ ] $\frac{di(t)}{dt} = \frac{\bar{k}\beta}{\mu} i(t)(1-i(t))$
- [ ] $\frac{di(t)}{dt} = (\bar{k}\beta - \mu) i(t)(1-i(t))$

---

### Q3 — Multiple choice (1 point)

What is the relation that determines the percentage of the population that will be infected once an endemic state is reached, according to the SIS model under the homogeneous mixing assumption?

- [ ] $1 + \frac{\mu}{\bar{k}\beta}$
- [ ] $1 - \frac{\bar{k}\beta}{\mu}$
- [ ] $1 - \bar{k}\beta\mu$
- [ ] $1 - \frac{\mu}{\bar{k}\beta}$

---

### Q4 — Fill in the Blank (1 point)

The reproductive number $R_0$ represents the average number of secondary infections that will arise from a single infected individual in the susceptible population. What are the two major factors that this number depends on (please select those two major factors to True. Otherwise, make the option False)?

1. The average attack rate of the pathogen — `True` / `False`
2. The primary transmission method — `True` / `False`
3. The average number of contacts each infected individual has — `True` / `False`
4. The average amount of time an individual remains infectious — `True` / `False`

---

### Q5 — Multiple choice (1 point)

Which of the following is true about superspreading events (SSEs)?

- [ ] Superspreading events only happen if R0 is large
- [ ] If an infection network has a "Poisson-like" degree distribution, it will still have superspreading events
- [ ] SSEs have only been observed rarely in practice
- [ ] SSEs can be caused by individuals with a very large number of contacts

---

### Q6 — Fill in the Blank (1 point)

Which contact network attributes cannot be captured by the degree block approximation? (If it cannot be captured, select True in that corresponding option)

1. Network assortativity — `True` / `False`
2. Network community structure — `True` / `False`
3. The degree distribution is a power-law — `True` / `False`
4. The degree distribution is a truncated power-law — `True` / `False`
