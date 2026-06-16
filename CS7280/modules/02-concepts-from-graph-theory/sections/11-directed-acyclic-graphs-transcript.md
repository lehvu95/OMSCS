# Directed Acyclic Graphs (DAGs)

| Text |
|------|
| A special class of directed graphs that is common in network science is those that do not  |
| have any cycles. They are referred to as directed acyclic graphs or DAGs. DAGs are common  |
| because they represent generalized hierarchy. And dependency networks in a generalized  |
| hierarchy and node may have more than one parent. An example of a dependency network is  |
| the prerequisite relations between college courses. We say that a directed network has a  |
| topological order, if we can run its nodes so that every adds points from a node of lower  |
| rank to a node of higher rank. This visualization shows the concept of a directed acyclic  |
| graph for a network with six nodes, and as you can see at the bottom, there is a  |
| topological order for this network, right? In which all the edges point from nodes at the  |
| left to notes at the right. In other words, from nodes that are lower rank, to nodes that  |
| are higher rank. Here is a set of important facts about DAGs. First if a directed network  |
| has a topological order then it must be a DAG. Second, a DAG must include at least one  |
| source node. In other words a node with zero incoming edges. And third, if a graph is a  |
| DAG, then it must have a topological ordering, in other words directed network, has  |
| topological order if and only, it is a DAG. Here is how you can show the third property,  |
| that if a network is a DAG, then it must have a topological ordering. As we saw, if the  |
| network is a DAG, then it must have at least one source. So the first step of the  |
| algorithm is that we start from a source node s, in this example, as you can see, the DAG  |
| has two sources nodes A and G. Let's suppose for example that you start from node G. The  |
| next step of the algorithm is that you remove that source node, you remove g in this  |
| case, and also remove all the edges of that node. And so you decrement the indegree of  |
| all the nodes that that source was pointing to. The graph now is still a DAG. As you can  |
| see, after we have removed the source G, then you repeat the previous steps you choose a  |
| new source, in this case, source A, remove it, remove the edges of that node, and you  |
| repeat every time you identify the next node in the Topological Ordering. So here the  |
| source is B, you remove that. The next source is node E, you remove that and the process  |
| continues until you, you have basically removed all the nodes and all the nodes appear in  |
| the topological ordering. |
