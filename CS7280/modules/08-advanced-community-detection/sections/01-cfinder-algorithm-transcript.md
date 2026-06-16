# CFinder Algorithm

| Text |
|------|
| The CFinder algorithm was one of the first community. If k is equal to 3, the CFinder  |
| algorithm tries to identify all triangles, which is what we see here. Two k cliques are  |
| considered overlapping, if they share k minus one nodes. Two triangles for instance are  |
| overlapping if they share a link. Consider the network in this visualization, there are  |
| five k cliques for k equal to 3. They overlap matrix O, shows which of these k cliques  |
| are overlapping. For example, cliques 1 and 2 are overlapping. If two k cliques share at  |
| least k minus one nodes, they are considered overlapping and the corresponding element of  |
| matrix O is 1 otherwise it is 0. Note that the green and purple k cliques are  |
| overlapping, as well as the gray orange and blue cliques. The communities that the CFnder  |
| algorithm discovers are the connected components in this k cliques network, which is what  |
| we see in part c. Part d shows the two discovered communities projected back to the  |
| original network. Note that there is one node in this case that belongs to two  |
| communities. That node participates in three k cliques. One k clique the purple belongs  |
| to the red community, while the two other k cliques, the green and the orange, belong to  |
| the blue community. Let's look now at a larger example. In part a, we said k=3 and  |
| discovered all triangles in the network. Part c shows that when k=3, we identify three  |
| communities, the green, the gray and the blue. Note that the green and the blue share a  |
| node. What would happen if we said k=4? Now we first compute all the four node cliques,  |
| part b shows just one of them. Recall that two four node cliques are adjacent if they  |
| share three nodes. This visualization shows a different toy network and the resulting set  |
| of communities when we said k=4. After computing all four node cliques, we see here that  |
| there are four connected components of four cliques, each of them corresponding to a  |
| community. The four orange nodes here belong to more than one community. |
