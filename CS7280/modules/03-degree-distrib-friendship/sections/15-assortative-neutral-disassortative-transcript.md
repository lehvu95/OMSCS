# Assortative, Neutral and Disassortative Networks

| Text |
|------|
| Let's look at some examples of science degree correlation plots from real world networks. |
| The first network refers to the collaboration between a group of scientists, two nodes, |
| two scientists are connected if they have written at least one research paper together. |
| Notice that the data is quite noisy especially when the degree K is more than about 70. |
| The reason simply that we did not have a large enough sample of such nodes with large |
| degrees. Nevertheless, we clearly see a positive correlation between the degree K and the |
| degree of the nearest neighbor, which is shown in the y axis. If we model the data with a |
| power law relation, the exponent mu is approximately 0.37 in this case. We can use this |
| value to quantify and compare the sort of activity of different networks when the |
| estimate of mu is statistically significant. The second network refers to a portion of |
| the power grid in the United States. The data in this case does not support a strong |
| correlation between the degree K and the degree of the nearest neighbor. So it is safe to |
| assume that this network is what we call neutral. The third network refers to a metabolic |
| network where nodes here are metabolites. And they are connected. If two metabolites A |
| and B appear in the opposite sides of the same chemical reaction in a biological cell, |
| the data so a strong negative correlation in this case. But only if the nodes have degree |
| 5, 10, or higher. If we model the data with power law relation, the exponent mu is |
| approximately minus 0.76. This suggests that complex metabolites such as glucose, are |
| either synthesised through a process called anabolism. Or broken down into, through a |
| process called catabolism into a large number of simpler molecules such as carbon dioxide. |
