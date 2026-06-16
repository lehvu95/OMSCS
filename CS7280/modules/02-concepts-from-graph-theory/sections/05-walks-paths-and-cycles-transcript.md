# Walks, Paths and Cycles Part One

| Text |
|------|
| A walk from a node S to a node T in a graph is a sequence of successive edges that starts  |
| at S and ends at T. A walk may visit the same node more than once. For example, here you  |
| see a walk that visits node C more than once. A path is a work in which the intermediate  |
| nodes are distinct. For example, the path from C to E to F does not visit the same node  |
| more than once. A cycle on the other hand, is a path that starts and ends at the same  |
| node. For instance, here we have a cycle between nodes B,C, and D. |

# Walks, Paths and Cycles Part Two

| Text |
|------|
| In the visualization that you see, we're asking how many works of length-3 are there from  |
| node A to node C or from A to node D in this graph? The answer is given by the element sd  |
| of the matrix A to the kth power, where k is the walk length. So what you see in this  |
| visualization shows the cubic power of the adjacency matrix A. And that shows there are  |
| four walks actually of length-3 from A to C, the walks ABDC, ABAC, ACAC and ACDC. On the  |
| other hand, as you can see, the number of walks of length-3 from A to D is 0. There are  |
| no walks of length-3 that can take you from node A to node D. |
