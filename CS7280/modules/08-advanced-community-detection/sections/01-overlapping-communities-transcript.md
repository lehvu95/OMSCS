# Overlapping Communities

| Text |
|------|
| In practice, it is often the case that the network node may belong to more than one  |
| communities. Think of your social network. For instance, you probably belong to a  |
| community that covers mostly your family, another community of colleagues or classmates,  |
| a community of friends, and so on. This simple observation raises doubts about our  |
| fundamental assumption that we can partition the nodes of a network in non-overlapping  |
| communities. For instance, look here at the network of words from the South Florida Free  |
| Association Network. Two words are connected here if their meaning is somehow related.  |
| For example, the word Einstein is associated with the word scientist, science, inventor,  |
| genius, gifted, smart, and others. At the lower right part of the figure, we see a dense  |
| community of nodes in blue. Most of them relate to colors. The green nodes, on the other  |
| hand, form another community, this time related to astronomy. It is important to note,  |
| however, that there are few nodes that participate in more than one community. For  |
| example, the word bright is associated with the intelligence community, the astronomy  |
| community, the colors community, and the light community. How can we identify communities  |
| in a network allowing the possibility that the node may belong to more than one  |
| community? In the following, we will review a couple of algorithms that can do exactly  |
| that. |
