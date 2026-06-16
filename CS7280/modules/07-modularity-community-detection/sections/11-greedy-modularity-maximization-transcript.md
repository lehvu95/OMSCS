# Greedy Modularity Maximization

| Text |
|------|
| The problem of modularity maximization is NP-Hard, meaning that we cannot solve it  |
| efficiently unless, if it turns out that P is equal to NP. One of the most commonly used  |
| algorithms for community detection is the following greedy heuristic. First, the  |
| algorithm starts by assigning a community to each node. Then in every iteration, we  |
| select the two communities A and B, that when merged, they result in the largest  |
| modularity increase. This is where we use the formula that we derived in the previous  |
| page. After these two communities are merged, the algorithm repeats the previous  |
| iteration until we have a single community. This process creates a dendrogram in a  |
| bottom-up manner, similar to the agglomerative hierarchical clustering algorithm we saw  |
| earlier. The difference is that in each step, we merge the two communities that result in  |
| the largest modularity increase. After the complete dendrogram is constructed, we select  |
| the branching point of the dendrogram that results in the maximum modularity. |
