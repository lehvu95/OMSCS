# Network Sampling Strategies

| Text |
|------|
| There are various ways to sample from a network and they result in subgraphs with very  |
| different properties. Here we introduce four of the most common network sampling  |
| strategies. Suppose that the network has n nodes and we want to sample k of them. The  |
| simplest sampling strategy is to choose randomly and without replacement k out of n  |
| nodes. And Ned's of the original network is included in the sample only if both its end  |
| points are sampled. In this example, the yellow nodes are the K sampled nodes, but the  |
| only sampled edges are those highlighted in orange. This is referred to as induced  |
| subgraph sampling. Suppose now that the network has m edges and we want to sample k of  |
| them. Another simple sampling strategy is to select randomly and without replacement k  |
| edges. And now it is included in the sample as long as it is adjacent or incident to a  |
| sampled edge. This is why this method is referred to as incident subgraph sampling. In  |
| this visualization, the yellow edges have been sampled while the orange nodes are  |
| included in the sample because they are adjusting to at least one sampled edge. Note that  |
| higher degree nodes are more likely to be sampled this way. In other words, this is a  |
| biased sampling strategy in terms of node sampling probabilities. Another sampling  |
| strategy referred to as snowball sampling is to start from a set of randomly selected  |
| nodes referred to as seeds sown in yellow here. In the first wave of the process, we  |
| include in the sample all the nodes and edges that are adjacent to the seeds. These are  |
| shown in orange. In the second wave, we include all the nodes and edges that are adjacent  |
| to the notes of the first wave and that have not been sampled already. Bees are shown in  |
| red. This process continues until we have included in the sample a desirable number of  |
| nodes or edges. Or we have reached the point in which we cannot sample anymore. The  |
| special case of a single sampling wave is referred to as star sampling. Another family of  |
| sampling strategies is referred to as link tracing. It is similar with snowball sampling  |
| in the sense that we start from some seed nodes. But here we denote sample all the edges  |
| and nodes. Instead, there is a criterion that specifies which adjusts and note to sample  |
| at each step. For instance, in computer networks, we can perform a trace route sampling.  |
| Here the seeds that are sown in yellow as S1 and S2 are referred to as the source nodes  |
| of the trace routes. And we are also given a set of target nodes. So here is T1 and T2.  |
| The network uses a specific route to connect a source to a target. And that is exactly  |
| the sequence of nodes and edges we include in the sample. So in here in orange, the  |
| sample in this case depends both on the chosen sources and targets, but also on the  |
| routing strategy that is deployed in that network. |
