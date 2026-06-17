# Lesson 3 Recommended Reading — Topic Summary

> Source: CS-7280-O01, OAN (Summer 2026) — Lesson 3 supplementary reading

## Summary

The single Lesson 3 reading grounds the lecture's recurring sexual-contact-network example in a concrete empirical study. Lesson 3 introduces degree distributions, their moments, and the heavy-tailed degree distribution of sexual-contact networks (the canonical example of a real network whose second moment is large), then connects degree heterogeneity to the friendship paradox and immunization strategies. This reading takes a real, time-resolved sexual-contact network — 50,185 contacts from high-end prostitution — and asks what actually governs epidemic spread on it: the network topology, the contact-rate (degree) distribution, or the *temporal* ordering of contacts.

The unifying message is that degree distribution alone is not the whole story. The authors simulate SI and SIR spreading on the empirical temporal network and compare against randomized, mean-field, and static-network baselines. They find that the heavy-tailed contact-rate distribution (the degree-distribution effect the lesson emphasizes) and the temporal correlations push in opposite directions: temporal correlations accelerate outbreaks in the early phase, while the network topology beyond the contact-rate distribution tends to slow them down. The result is a well-defined, rather high epidemic threshold and a broad distribution of outbreak sizes even at maximal per-contact transmission probability.

The key takeaway: the degree (contact-rate) distribution is a first-order determinant of spreading, exactly as Lesson 3 argues, but a full account of real epidemics also needs the temporal structure of contacts — a caveat that anticipates the epidemic-threshold and degree-block material in Lesson 9.

## Details

- **Simulated epidemics on an empirical temporal sexual network.** [[Simulated Epidemics in an Empirical Spatiotemporal.pdf]] (Luis E. C. Rocha, Fredrik Liljeros, Petter Holme, *PLoS Computational Biology* 7(3):e1001109, 2011) simulates SI and SIR models on a temporal network of 50,185 sexual contacts. The contact-rate distribution is heavy-tailed — the empirical realization of the skewed sexual-contact degree distribution discussed in the "Example: Degree Distribution of a Sex-Contact Network" section. Comparing the real temporal data to data randomizations isolates the effect of *when* contacts occur from *who* contacts *whom*: temporal correlations speed up the early growth of outbreaks, whereas the network topology (controlling for the contact-rate distribution) slows spread relative to a mean-field expectation. The network exhibits a relatively high epidemic threshold and a broad outbreak-size distribution, and the authors note the studied form of commercial sex is not a major HIV reservoir.

## Examples

- **Contact-rate heterogeneity** — the heavy-tailed number of partners per individual is the degree distribution Lesson 3 uses to motivate moments and the friendship paradox; here it sets the baseline epidemic potential.
- **Temporal vs. static comparison** — running the same SI/SIR dynamics on the real ordered contacts versus a time-shuffled version shows temporal correlations accelerating the early epidemic, a structure invisible to a purely degree-distribution view.

## References

- [[Simulated Epidemics in an Empirical Spatiotemporal.pdf]] — L. E. C. Rocha, F. Liljeros, P. Holme, *Simulated Epidemics in an Empirical Spatiotemporal Network of 50,185 Sexual Contacts*, PLoS Computational Biology 7(3):e1001109, 2011 — <https://doi.org/10.1371/journal.pcbi.1001109>
