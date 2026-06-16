# Lesson 6 Recommended Reading — Topic Summary

> Source: CS-7280-O01, OAN (Summer 2026) — Lesson 6 supplementary readings

## Summary

The Lesson 6 readings extend the lecture material on centrality and network-core metrics into three research-level treatments: how to test rigorously whether a network has a rich-club, how block-model community structure (including core-periphery topologies) evolves in the human connectome, and how path-centrality over a directed acyclic dependency network reveals an "hourglass" core. Each paper takes a metric introduced informally in the lessons — the rich-club coefficient, core-periphery organization, and the core set of nodes in DAGs — and develops it into a quantitative, statistically grounded method applied to real systems.

The unifying thread is the identification and validation of a *small, important set of nodes* against a principled null model. The rich-clubness paper formalizes when a dense club of high-degree nodes is statistically significant rather than an artifact of the degree sequence; the hourglass paper defines the network core as the smallest vertex set covering nearly all source-to-target dependency paths and compares it to a degree-preserving "flat" baseline; the connectome paper uses weighted stochastic block models to detect community topologies — modular, disassortative, and core-periphery — that plain modularity maximization misses. In every case the headline finding only becomes meaningful relative to an appropriate randomized comparison.

The key takeaway: node-importance and network-core metrics are claims about structure that must be measured against a null model. The same caution that motivates the lecture's treatment of centrality variants — that raw scores are not self-interpreting — recurs here as the difference between observing a rich-club, a core-periphery split, or an hourglass waist and demonstrating that it is statistically real.

## Details

- **Rich-clubness as a hypothesis test.** The rich-club coefficient $\phi(k)$ measures how densely the nodes with degree above $k$ connect among themselves. Because high-degree nodes connect more often by chance, a raw $\phi(k)$ must be normalized against a null model. [[rich-clubness-test.pdf]] introduces a null model with a lower rich-club coefficient, a normalization of $\phi(k)$ against that null, and a statistical test that uses the maximum deviation of the normalized coefficient to assign a single $p$-value of rich-clubness to a network — the first attempt to quantify rich-clubness with one significance value.
- **Path-centrality and the hourglass core.** [[hourglass-effect-hierarchical-dependency-networks.pdf]] analyzes the number of source-to-target dependency paths traversing each vertex (path centrality) and defines the **core** as the smallest set of vertices that collectively cover almost all dependency paths. A network has the **hourglass property** when this core is much smaller than that of a degree-preserving "flat" network with the same source dependencies. The proposed **Reuse Preference** model explains the effect: new modules preferentially reuse intermediate modules of similar complexity rather than connecting directly to sources, producing a narrow "waist."
- **Core-periphery and block structure in the connectome.** [[weighted-stochastic-block-models-connectome.pdf]] adopts weighted stochastic block models (WSBM), which split nodes into blocks that are stochastically equivalent in how they connect to the rest of the network. Unlike modularity maximization — which only finds assortative modules — WSBM can represent modular, disassortative, **core-periphery**, and mixed topologies. Applied to the human connectome across ages 6–85, WSBM communities are more hemispherically symmetric and spatially less compact than modularity communities, with the most significant age-related changes in prefrontal subregions.

## Examples

- **Rich-club in transportation and neural networks** — the rich-clubness test is motivated by systems where a tight club of hubs governs function: air-transportation backbones and the densely interconnected high-degree regions of brain networks.
- **Hourglass waist in technological and biological systems** — the hourglass framework is applied across technological, natural, and information dependency networks (e.g., software call graphs, metabolic and gene networks), each exhibiting the core/waist property to a different degree.
- **Core-periphery in the human connectome** — WSBM recovers core-periphery and disassortative blocks in anatomical brain networks that modularity maximization, restricted to assortative communities, cannot express.

## References

- [[rich-clubness-test.pdf]] — Alessandro Muscoloni & Carlo Vittorio Cannistraci, *Rich-clubness test: how to determine whether a complex network has or doesn't have a rich-club?* — <https://arxiv.org/abs/1704.03526>
- [[hourglass-effect-hierarchical-dependency-networks.pdf]] — *The Hourglass Effect in Hierarchical Dependency Networks*, Network Science 5(4):490–528, 2017 — <https://www.cambridge.org/core/journals/network-science/article/hourglass-effect-in-hierarchical-dependency-networks/DDBCA83D16CA74B827DAB66A98CC906A>
- [[weighted-stochastic-block-models-connectome.pdf]] — *Weighted Stochastic Block Models of the Human Connectome across the Life Span*, Scientific Reports, 2018 — <https://www.nature.com/articles/s41598-018-31202-1>
