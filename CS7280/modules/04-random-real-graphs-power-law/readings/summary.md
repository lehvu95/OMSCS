# Lesson 4 Recommended Reading — Topic Summary

> Source: CS-7280-O01, OAN (Summer 2026) — Lesson 4 supplementary reading

## Summary

The single Lesson 4 reading is the methodological backbone of the lecture's "How to Check for a Power Law" section. Lesson 4 establishes that many real networks have heavy-tailed, approximately power-law degree distributions, discusses the role of the exponent, and warns that naively fitting a line to a log-log degree plot is unreliable. This reading is the paper the lesson points to for doing it correctly: a principled statistical framework for deciding whether empirical data plausibly follow a power law, and for estimating the exponent and the lower cutoff if they do.

The unifying point is that "looks straight on a log-log plot" is not evidence of a power law. Least-squares fitting of logarithmically binned histograms produces biased exponent estimates and, worse, never tests whether the power-law hypothesis holds at all. The authors replace this with maximum-likelihood estimation of the scaling exponent $\alpha$ and the lower bound $x_{min}$, a Kolmogorov–Smirnov goodness-of-fit test (via synthetic-data resampling to produce a $p$-value), and likelihood-ratio tests that compare the power law against alternative heavy-tailed distributions (log-normal, exponential, stretched exponential, power-law with cutoff).

The key takeaway: claiming a network is "scale-free" requires this three-step discipline — MLE fit, goodness-of-fit $p$-value, and a likelihood-ratio comparison against competing distributions — because many heavy-tailed datasets that appear power-law are fit at least as well, or better, by other distributions. This is exactly the rigor the lesson asks students to apply instead of eyeballing the degree plot.

## Details

- **Power-law distributions in empirical data.** [[power-law-distributions-in-empirical-data.pdf]] (Aaron Clauset, Cosma Rohilla Shalizi, M. E. J. Newman, *SIAM Review* 51(4):661–703, 2009) presents a complete recipe for power-law analysis. (1) **Estimation:** maximum-likelihood estimators for the exponent $\alpha$ given a lower bound $x_{min}$, with $x_{min}$ itself chosen to minimize the KS distance between data and fitted model — avoiding the bias of least-squares on binned data. (2) **Goodness of fit:** a $p$-value computed by comparing the observed KS statistic to those of many synthetic datasets drawn from the fitted model; a small $p$-value rejects the power law. (3) **Model comparison:** Vuong-style likelihood-ratio tests against log-normal, exponential, stretched-exponential, and power-law-with-exponential-cutoff alternatives, since a passing goodness-of-fit test does not mean the power law is the *best* description. Applied to two dozen real datasets, the paper finds many "power laws" in the literature are statistically weak once tested this way. It is the method behind the lesson's `aaronclauset.github.io/powerlaws` reference.

## Examples

- **MLE vs. least-squares** — on synthetic power-law data, the least-squares log-log slope is systematically biased, while the MLE recovers the true exponent; the lesson's caution against line-fitting the degree plot is this result.
- **Goodness-of-fit $p$-value** — resampling synthetic datasets from the fitted model yields a $p$-value for the power-law hypothesis; e.g., several canonical "scale-free" datasets fail to reject simpler alternatives.
- **Likelihood-ratio comparison** — testing power law against log-normal frequently cannot distinguish the two from realistic sample sizes, tempering strong "scale-free" claims.

## References

- [[power-law-distributions-in-empirical-data.pdf]] — A. Clauset, C. R. Shalizi, M. E. J. Newman, *Power-Law Distributions in Empirical Data*, SIAM Review 51(4):661–703, 2009 — <https://doi.org/10.1137/070710111> (arXiv: `0706.1062`).
