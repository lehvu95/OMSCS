# Random Removal vs Targeted Removal

| Text |
|------|
| Consider two ways of removing nodes from a network. Random removals or failures, and  |
| targeted removals of the highest degree nodes. We refer to those as attacks. The  |
| visualization shows a network with 50 nodes and about 100 pages. The network was created  |
| with the preferential attachment model. So that the good distribution is approximately a  |
| power-law with exponents three, as we learned in lesson four, note that the size of its  |
| node is proportional to its degree. The animation shows the case of random removals. In  |
| its duration, we select a random node and remove it. This changes the degree of all nodes  |
| connected to the removed node. The question we focus on is, how many nodes do we need to  |
| remove until the network's largest connected component falls apart to just a small  |
| fraction of the initial network size. In this animation. This happens after we remove  |
| about 40 to 45 out of the 50 nodes. Note that the four to five halves keep the network  |
| are connected because of their many connections. The largest connected component breaks  |
| down only when we have removed so many nodes. But the original hubs are no longer high  |
| degree nodes. Let us now switch to targeted removals or attacks. The animation shows here  |
| what happens if we remove the node with the highest degree in its duration? Such an  |
| attack on the network would require that the attacker has some information about the  |
| topology of the network or the degree of each node. In this case, it takes only the  |
| removal of about ten nodes before the largest connected component falls apart. Two  |
| disconnected individual nodes, and few small connected components. The qualitative  |
| conclusion from these two animations is that networks with power-law degree distribution  |
| and thus with hubs are quite robust to random failures. But they are also very vulnerable  |
| to targeted attacks on their highest degree nodes. |
