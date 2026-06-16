# Modular Networks: The Adjacency Matrix View

| Text |
|------|
| In order to make the community detection problem well defined, we need to add some  |
| additional constraints. Before we address this question, it is good to reflect on some  |
| high level questions regarding communities. Should we expect that each node belongs to a  |
| community? What if some nodes do not belong to any community? Is it necessary that the  |
| communities should be non-overlapping? What if some nodes belong to more than one  |
| community? And we should not expect that every network has communities. In particular, if  |
| a network is made of random connections, it may still have some small densely connected  |
| sub graphs depending on the graph density. It would not make sense to claim that sets a  |
| network has an interesting community structure however. So how should we avoid  |
| discovering communities that are formed strictly by chance? We will return to these  |
| questions later in this lesson as well as at the next lesson. Another way to think about  |
| network communities and visualize that presence is through the adjacency matrix. Suppose  |
| that there are k non-overlapping groups of nodes of potentially different sizes, so that  |
| the density of the internal connections within its group is much greater than the density  |
| of external connections. If we reorder the adjacency matrix of the network, so that the  |
| nodes of its group appear in consecutive rows, we will observe that the adjacency matrix  |
| includes k dense sub matrices one for each community. The rest of the adjacency matrix is  |
| not completely zeros, but it is much more sparsely populated. This is shown in the  |
| visualization for a network with four communities, the red, the blue, the green, and the  |
| yellow. In this case, all four communities have the same size. The probability that two  |
| nodes of the same community are connected is 50%. The density of the external edges is  |
| only 10%. For comparison, we also saw a reference network in which the connection  |
| probabilities is the same for all pairs of nodes, and the total number of edges is the  |
| same as in the first row. Clearly, the second network, the random one, doesn't have  |
| communities, and the adjacency matrix cannot be represented in the blog structure we show  |
| earlier. |
