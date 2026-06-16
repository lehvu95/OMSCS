# Community Detection Problem

| Text |
|------|
| In the community detection problem, we also need to partition the nodes of a graph into a  |
| set of non-overlapping clusters or communities. But the key difference is that we do not  |
| know a priority, how many sides communities exist? And there is no requirement that they  |
| have the same size. What is the key property of its community? Loosely speaking, the  |
| nodes within its community should form a densely connected subgraph. Of course, this is  |
| not a mathematically precise definition because it does not specify how densely the  |
| community subgraphs would be. One extreme point would be to require that each community  |
| is a maximally sized clique. In other words, a complete subgraph that cannot be increased  |
| any further. Here in this visualization, we see a clinic-based community with four orange  |
| nodes. This is a stringent definition. However, it does not capture the pragmatic fact  |
| that some edges between nodes of a community may be missing. So another way to think of  |
| its community is S and approximate clique. A subgraph in which the number of internal  |
| edges, in other words, edges between nodes of the subgraph is much larger than the number  |
| of external edges, edges between nodes of that subgraph and the rest of the graph. This  |
| is again a rather loose definition. However, it does not tell us which community is  |
| better. The purple at the left or the green at the right. |
