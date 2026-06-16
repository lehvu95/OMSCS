# Watts Strogatz Model

| Text |
|------|
| How can we create networks that have this small-world property? One such model was |
| proposed by Watts and Strogatz in their 1998 paper that started when network science |
| field. The model starts with irregular network with the desired number of nodes and |
| average degree. The topology of the regular network is often the ring that we saw here. |
| With a small probability p, we select an edge and reassign one of its two star to a |
| randomly chosen node. As you see here, you may wonder, why do we expect that a small |
| fraction of randomized edges will have any significant effect on the properties of this |
| network. It turns out that even if this rewiring probability p is quite small, the |
| randomized edges provides shortcuts that reduce the length of the shortest paths between |
| node pairs. As we will see next, even a small number of such sort cats, meaning a |
| rewiring probability p close to 1% is sufficient to reduce the characteristic path length |
| and the diameter down to the same level with a corresponding random GNP network. At the |
| same time, the wired network is still highly clustered at the same level with the regular |
| network we started from. As long as p, of course is quite small. If this rewiring |
| probability p were set to one, we would end up with a random GMP graph, which is what we |
| see at the right. Network, would have even shorter paths, but it would not have any |
| significant clustering. There have been analytical studies of the Watts-Strogatz Model |
| that derived the clustering coefficient or the diameter as a function of the rewiring |
| probability P. For our purposes, it is sufficient to see some simulation results only. |
| The visualization here refers to a network of a thousand nodes with an average degree of |
| ten. It also shows the average clustering coefficient normalized by the corresponding |
| coefficient when p is equal to 0 with green dots. The plot also shows the average path |
| length with purple dots, also normalized by the corresponding metric when p is equal to |
| 0. Note the logarithmic scale on the x-axis. As you see, when p is close to 1%, the |
| clustering coefficient is still almost the same as the regular network we started with. |
| And the average path length is close to what we would expect from a random graph. |
