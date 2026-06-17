# Analysis of Preferential Attachment Model

| Text |
|------|
| The recognition that most real-world networks, so dynamic growth and preferential  |
| connections, inspired a simple model called the Barabasi-Albert model or preferential  |
| attachment. It can generate networks with a power load degree distribution. The model is  |
| described as follows. We start with an initial number of nodes, the links between them  |
| are chosen arbitrarily as long as its node has at least one link. Now from that point on,  |
| the network develops following two steps at a time. In the growth step, a new node is  |
| added with m links. In this animation, m is equal to 2 and in the preferential attachment  |
| step, the probability that a link of the new node connects to a node i is proportional to  |
| the degree of node i. Preferential attachment is a probabilistic mechanism and you know  |
| this free to connect to any node in the network, whether it is a hub or it has only one  |
| link. The preferential attachment bias however implies that if a new node has a choice  |
| between, for example, a degree 2 and a degree 4 node, it is twice as likely that the new  |
| node will connect to the node of degree 4 rather than the node of degree 2. While most  |
| nodes in the network have only few links, a few nodes gradually become hubs. These hubs  |
| are the result of a reach gets richer phenomenon. Due to preferential attachment, new  |
| nodes are more likely to connect to the more connected nodes than to the smaller nodes.  |
| Hence the larger nodes will acquire links at the expense of the smaller nodes eventually  |
| becoming hubs. In the following pages, we will study this model more mathematically. |
