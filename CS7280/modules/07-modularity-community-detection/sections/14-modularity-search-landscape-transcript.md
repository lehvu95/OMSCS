# The Modularity Search Landscape

| Text |
|------|
| Here is an additional illustration of the modularity resolution HQ. Consider the  |
| network shown in the visualization. It is a ring network in which each member of the ring  |
| is a small community of five nodes, a small click. In the community assignment A, each of  |
| these five node clicks is a separate community which is the most intuitive partitioning  |
| in this case. The modularity of this community assignment is 0.867. This is not, however,  |
| the maximum modularity value. The subsequent two assignments have even larger modularity.  |
| While that shown in B is the maximum possible. Note that this assignment merges every two  |
| consecutive clicks into one community. An interesting observation, however, is that the  |
| modularity of A is not much lower than the maximum modularity. One is 0.867, the other is  |
| 0.871. It turns out that this is common in practice. First, computing the maximum  |
| modularity value is very hard computationally, it is an NP-hard problem and second, the  |
| maximum modularity value may not correspond to the most intuitive community assignment  |
| due to this modularity resolution HQ. However, what often happens is that the maximum  |
| modularity value resides in a plateau, as we see here. And it is not much higher than  |
| other local maxima that correspond to different community assignments. Consequently, even  |
| though we rarely know the optimal solution to the modularity maximization problem, the  |
| various heuristics we saw earlier can typically compute reasonable solutions that also  |
| reside in that modularity plateau. |
