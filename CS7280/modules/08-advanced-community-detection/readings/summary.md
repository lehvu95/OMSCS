# Lesson 8 Recommended Reading — Topic Summary

> Source: CS-7280-O01, OAN (Summer 2026) — Lesson 8 supplementary readings

## Summary

The Lesson 8 readings extend the lecture into two advanced community-detection settings that the basic modularity framework cannot handle: communities that **change over time** and communities that must be **inferred from spatio-temporal data** rather than read off a given graph. The first reading, an Encyclopedia of Social Network Analysis and Mining entry on dynamic community detection, surveys how communities are tracked across the successive snapshots of an evolving network. The second, the δ-MAPS paper, develops the spatially-contiguous, overlapping-domain method introduced in the δ-MAPS sections of this lesson and applies it to climate and brain data.

The unifying thread is that "a community" is no longer a static partition of a fixed node set. In the dynamic case the challenge is identity and continuity — matching communities found in one time step to those in the next, and naming the operations (birth, death, growth, contraction, merge, split) by which they evolve. In the δ-MAPS case the challenge is upstream of detection entirely: the nodes themselves (spatially contiguous "domains") must first be discovered from correlated time series, allowed to overlap, and then connected by lagged, statistically significant functional edges. Both readings emphasize validation against an appropriate baseline and the limitations of naively applying static modularity maximization.

The key takeaway: advanced community detection is defined by what the basic methods leave out — temporal evolution, overlap, and the inference of structure from raw measurements. These readings ground the lesson's treatment of dynamic communities, overlapping communities, and the δ-MAPS algorithm.

## Details

- **Dynamic / temporal community detection.** [[dynamic-community-detection.pdf]] (Cazabet & Amblard, *Encyclopedia of Social Network Analysis and Mining*) defines temporal community detection as finding the relevant communities corresponding to each step of evolution of a network that changes over time. It formalizes **dynamic communities** and the **operations** on them across snapshots — communities can appear, disappear, grow, shrink, merge, and split — and contrasts the main algorithmic strategies for maintaining community identity across time (e.g., independent detection followed by matching, versus methods that smooth or constrain successive partitions). This is the reference behind the lesson's "Dynamic Communities – Approach #1/#2/#3" sections.
- **δ-MAPS: inferring overlapping domains and a lagged functional network.** [[delta-maps-spatiotemporal-functional-domains.pdf]] (Fountalis, Dovrolis, Bracco *et al.*, *Applied Network Science*, 2018) proposes a method that identifies spatially contiguous and possibly **overlapping** components ("domains") from spatio-temporal data and then infers a **weighted and lagged** functional network between them. δ-MAPS first locates the epicenters of activity of a domain, then grows each domain as the maximum set of spatially contiguous cells that include an epicenter and satisfy a **homogeneity constraint** (the "domain homogeneity constraint" section of the lesson). Edges between domains are added only when a lagged correlation is statistically significant under a multiple-testing correction, with each edge assigned a lag range and a weight. The paper situates δ-MAPS relative to clustering, multivariate statistics, and network community detection, and argues it avoids several known limitations of those methods.

## Examples

- **Evolving social and collaboration networks** — the dynamic-community reading frames its operations (merge, split, growth) in terms of networks whose nodes and edges are added and removed over time, the setting for tracking communities across snapshots.
- **Climate teleconnections** — applied to sea-surface temperature data, δ-MAPS recovers well-known teleconnections such as the lagged link between the El Niño Southern Oscillation and the Indian Ocean (the lesson's "Application in Climate Science").
- **Functional brain networks** — applied to resting-state fMRI cortical data, δ-MAPS confirms known resting-state networks (default mode, occipital, motor/somatosensory, auditory) and reveals a densely interconnected backbone of a few cortical regions.

## References

- [[dynamic-community-detection.pdf]] — Rémy Cazabet & Frédéric Amblard, *Dynamic Community Detection*, Encyclopedia of Social Network Analysis and Mining, 2014 — <https://doi.org/10.1007/978-1-4614-6170-8_383>
- [[delta-maps-spatiotemporal-functional-domains.pdf]] — I. Fountalis, C. Dovrolis, A. Bracco *et al.*, *δ-MAPS: from spatio-temporal data to a weighted and lagged network between functional domains*, Applied Network Science 3:21, 2018 — <https://doi.org/10.1007/s41109-018-0078-z>
