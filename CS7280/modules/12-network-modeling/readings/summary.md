# Lesson 12 Recommended Reading — Topic Summary

> Source: CS-7280-O01, OAN (Summer 2026) — Lesson 12 supplementary readings

## Summary

The Lesson 12 readings cover the two ends of the network-modeling spectrum the lesson develops: optimization-driven formation and statistically-estimated hierarchical structure. The Fabrikant–Koutsoupias–Papadimitriou paper is the rigorous treatment of the cost-versus-path-length optimization model from the "Optimization-based Network Formation Model" sections, proving that a heuristically optimized trade-off between connection cost and centrality produces power-law degree distributions. The Clauset–Moore–Newman Nature paper is the source of the Hierarchical Random Graph (HRG) model that anchors the final third of the lesson — its dendrogram representation, maximum-likelihood probability estimation, and the MCMC search over dendrograms, applied to predicting missing links. A supplementary slide deck restates the Fabrikant HOT argument in lecture form.

The unifying thread is the lesson's central caution: very different mechanisms can produce the same statistics. Preferential attachment, link-copy, and heuristically optimized trade-offs all yield power-law degree distributions, so observing a power law says little about the generating mechanism. The HRG reading takes the complementary view — rather than positing a mechanism, it fits a flexible probabilistic model to a single observed network and uses it for prediction (missing/spurious edges) and ensemble generation. Together the readings span the two reasons to model a network: to *explain* how structure could arise (HOT optimization) and to *describe/predict* a given structure parsimoniously (HRG).

The key takeaway: a model's value lies in its purpose, not its realism. The HOT model explains power laws as an optimization by-product; the HRG model turns a single noisy network into a generator and a link predictor. Both make the lesson's George Box point concrete — "all models are wrong, but some are useful".

## Details

- **Heuristically Optimized Trade-Offs: A New Paradigm for Power Laws in the Internet.** [[heuristically-optimized-tradeoffs-power-laws.pdf]] (Alex Fabrikant, Elias Koutsoupias, Christos H. Papadimitriou, ICALP 2002) gives the rigorous analysis of the optimization-based formation model in the lesson. Each arriving node $i$ connects to the existing node $j$ minimizing $\delta\, d_{i,j} + h_j$ — a trade-off between Euclidean connection cost and hop-distance to the center. The paper proves that for $\delta$ below a constant the network is a star (hub-and-spoke), for $\delta$ growing faster than $\sqrt{N}$ it is a bounded-degree tree, and for the intermediate regime the degree distribution is heavy-tailed (power-law-like). It is the formal basis for the lesson's claim that optimization, with no randomness, can generate power laws. The companion slide deck [[heuristically-optimized-tradeoffs-slides.pdf]] presents the same argument in lecture form.
- **Hierarchical structure and the prediction of missing links in networks.** [[hierarchical-structure-prediction-missing-links.pdf]] (Aaron Clauset, Cristopher Moore, M. E. J. Newman, Nature 453, 2008) introduces the **Hierarchical Random Graph (HRG)** model behind the "Hierarchical Graph Model", "MLE of HRG Probabilities", "How to Find the Optimal Dendrogram", and "HRG Applications" sections. A network is modeled by a dendrogram $D$ (binary tree over the $n$ nodes) with a connection probability $p_r$ at each internal node $r$. Given $D$, the maximum-likelihood estimate is $\hat{p}_r = E_r/(L_r R_r)$; the optimal dendrogram is sampled by an ergodic MCMC with the Metropolis-Hastings rule, drawing dendrograms in proportion to their likelihood. The fitted model generates network ensembles, serves as a null model, and — the paper's headline result — predicts missing (false-negative) and spurious (false-positive) edges in noisy network data.

## Examples

- **HOT optimization regimes** — on $N=10{,}000$ points in the unit square, $\delta < 1/\sqrt{2}$ yields a hub-and-spoke star, $\delta \gg \sqrt{N}$ yields an exponential-degree nearest-neighbor tree, and the intermediate regime yields hub-rich, power-law-like topologies.
- **HRG link prediction** — fitting the HRG to terrorist-association, grassland food-web, and metabolic networks, the model ranks non-edges by predicted probability and recovers held-out (missing) edges far better than chance, the basis for cleaning noisy biological/neuroscience network data.
- **HRG as a null model** — generating an ensemble from a single brain-network snapshot (e.g., healthy vs. schizophrenia samples) lets one test whether a new network belongs to either group.

## References

- [[heuristically-optimized-tradeoffs-power-laws.pdf]] — A. Fabrikant, E. Koutsoupias, C. H. Papadimitriou, *Heuristically Optimized Trade-offs: A New Paradigm for Power Laws in the Internet*, ICALP 2002 — <https://doi.org/10.1007/3-540-45465-9_11>
- [[hierarchical-structure-prediction-missing-links.pdf]] — A. Clauset, C. Moore, M. E. J. Newman, *Hierarchical Structure and the Prediction of Missing Links in Networks*, Nature 453, 2008 — <https://doi.org/10.1038/nature06830>
- [[heuristically-optimized-tradeoffs-slides.pdf]] — Lecture slide deck restating the Fabrikant et al. HOT model (supplementary).
