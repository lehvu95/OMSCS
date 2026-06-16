# Introduction to Modularity and Community Detection

| Text |
|------|
| We're now getting into a very interesting and practically important part of this  |
| course, community detection. Many real-world networks are modular, meaning that they  |
| consist of several modules or clusters of densely interconnected nodes referred to as  |
| communities. In this first lesson about community detection, we will discuss more clearly  |
| what the community means and contrast this problem with graph partitioning. Then we will  |
| review some popular algorithms for community detection. The simpler class of such  |
| algorithms is based on the notion of hierarchical clustering. We will also define a  |
| mathematical metric referred to as modularity. This metric quantifies the statistical  |
| significance of a community structure at the given network relative to a null model. In  |
| other words, a network in which the connections between nodes are completely random. The  |
| modularity metric also enables the design of more principled algorithms for community  |
| detection. The most common of which are the greedy or Louvain algorithms. We will also  |
| solve mathematically however, that the modularity metric has a fundamental limitation. It  |
| cannot detect communities that are smaller than a certain size. This is referred to as  |
| modularity resolution. We will close with a discussion of hierarchical modularity, in  |
| other words, communities within communities and how to detect them in a network. |
