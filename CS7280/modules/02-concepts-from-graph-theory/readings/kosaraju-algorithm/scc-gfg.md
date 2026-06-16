# Strongly Connected Components

> Source: https://www.geeksforgeeks.org/strongly-connected-components/ — GeeksforGeeks. (Implementations shown in Python; the source page also provides C++/Java/C#/JavaScript versions.)

In a directed graph, a Strongly Connected Component is a subset of vertices where every vertex in the subset is reachable from every other vertex in the same subset by traversing the directed edges. Finding the **SCCs** of a graph can provide important insights into the structure and connectivity of the graph, with applications in various fields such as **social network analysis, web crawling, and network routing**.

The below graph has two strongly connected components {1,2,3,4} and {5,6,7} since there is path from each vertex to every other vertex in the same strongly connected component. 

![[img/sccgfg-01.webp|600]]
Strongly Connected Components

\

- **Difference Between Connected and Strongly Connected Components (SCCs) :** The term Connected is for undirected graphs and Strongly Connected is for directed graphs. A subgraph of a directed graph is considered to be an Strongly Connected Components(SCC) if and only if for every pair of vertices A and B, there exists a path from A to B and a path from B to A.

<!-- -->

- **Connecting Two Strongly Connected Component by a Unidirectional Edge :** Two different connected components becomes a single component if a edge is added between a vertex from one component to a vertex of other component. But this is not the case in strongly connected components. Two strongly connected components d not become a single strongly connected component if there is only a unidirectional edge from one SCC to other SCC. Please refer the above graph for example. We have edges from 4 to 5 and 3 to 4, despite these edges, two components are different.

**Example:**

> **Input:** adj[][] = [[], [3, 4], [1], [2], [5], []]
>
>
> ![[img/sccgfg-02.webp|600]]
>
>
> **Output:** [[1, 2, 3], [4], [5]]\
> **Explanation:** There are 3 different Strongly Connected Components. They are {1, 2, 3} and {4}, {5}.

Try It Yourself

## [Naive Approach] Brute Force Approach

> The main idea will be for each vertex i, find the vertices which will be the part of strongly connected component containing vertex i. Two vertex i and j will be in the same strongly connected component if they there is a directed path from vertex i to vertex j and vice-versa.

Let's understand the approach with the help of following example:

![[img/sccgfg-03.webp|600]]
Brute Force Approach

- Starting with vertex 1. There is path from vertex 1 to vertex 2 and vice-versa. Similarly there is a path from vertex 1 to vertex 3 and vice versa. So, vertex 2 and 3 will be in the same Strongly Connected Component as vertex 1. Although there is directed path form vertex 1 to vertex 4 and vertex 5. But there is no directed path from vertex 4,5 to vertex 1 so vertex 4 and 5 won't be in the same Strongly Connected Component as vertex 1. Thus Vertex 1,2 and 3 forms a Strongly Connected Component.
- For Vertex 2 and 3, there Strongly Connected Component has already been determined.
- For Vertex 4, there is a path from vertex 4 to vertex 5 but there is no path from vertex 5 to vertex 4. So vertex 4 and 5 won't be in the Same Strongly Connected Component. So both Vertex 4 and Vertex 5 will be part of Single Strongly Connected Component.
- Hence there will be 3 Strongly Connected Component {1,2,3}, {4} and {5}.

Below is the implementation of above approach:

```
class GfG:
    # dfs Function to reach destination
    def dfs(self, curr, des, adj, vis):
        # If current node is the destination, return True
        if curr == des:
            return True
        vis[curr] = 1
        for x in adj[curr]:
            if not vis[x]:
                if self.dfs(x, des, adj, vis):
                    return True
        return False

    # To tell whether there is a path from source to destination
    def isPath(self, src, des, adj):
        vis = [0] * (len(adj) + 1)
        return self.dfs(src, des, adj, vis)

    # Function to return all the strongly connected components of a graph.
    def findSCC(self, n, a):
        # Stores all the strongly connected components.
        ans = []

        # Stores whether a vertex is a part of any Strongly Connected Component
        is_scc = [0] * (n + 1)

        adj = [[] for _ in range(n + 1)]

        for i in range(len(a)):
            adj[a[i][0]].append(a[i][1])

        # Traversing all the vertices
        for i in range(1, n + 1):
            if not is_scc[i]:
                # If a vertex i is not a part of any SCC, insert it into a new SCC list
                # and check for other vertices whether they can be part of this list.
                scc = [i]
                for j in range(i + 1, n + 1):
                    # If there is a path from vertex i to vertex j and vice versa,
                    # put vertex j into the current SCC list.
                    if not is_scc[j] and self.isPath(i, j, adj) and self.isPath(j, i, adj):
                        is_scc[j] = 1
                        scc.append(j)
                # Insert the SCC containing vertex i into the final list.
                ans.append(scc)
        return ans

if __name__ == "__main__":
    obj = GfG()
    V = 5
    edges = [
        [1, 3], [1, 4], [2, 1], [3, 2], [4, 5]
    ]
    ans = obj.findSCC(V, edges)
    print("Strongly Connected Components are:")
    for x in ans:
        for y in x:
            print(y, end=" ")
        print()
```

                    if not is_scc[j] and self.isPath(i, j, adj) and self.isPath(j, i, adj):

**Output**

    Strongly Connected Components are:
    1 2 3
    4
    5

**Time complexity: O((n^2) \* (n + m)),** because for each pair of vertices we are checking whether a path exists between them.\
**Auxiliary Space: O(N)**

## [Expected Approach 1] Using Kasaraju's Algorithm

1.  **Performing Depth-First Search (DFS) on the Original Graph**:
    - We first do a DFS on the original graph and record the finish times of nodes (i.e., the time at which the DFS finishes exploring a node completely).
2.  **Performing DFS on the Transposed Graph**:
    - We then reverse the direction of all edges in the graph to create the transposed graph.
    - Next, we perform a DFS on the transposed graph, considering nodes in decreasing order of their finish times recorded in the first phase.
    - Each DFS traversal in this phase will give us one SCC.

Let us take the following graph as an example. It has 3 strongly connected components.

![[img/sccgfg-04.webp|600]]
Connected Components

**How does this work?** The above algorithm does DFS two times. DFS of a graph produces a single tree if all vertices are reachable from the DFS starting point. Otherwise DFS produces a forest. So DFS of a graph with only one SCC always produces a tree. The important point to note is DFS may produce a tree or a forest when there are more than one SCCs depending upon the chosen starting point. For example, in the above diagram, if we start DFS from vertices 0 or 1 or 2, we get a tree as output. And if we start from 3 or 4, we get a forest. To find and print all SCCs, we would want to start DFS from vertex 4 (which is a sink vertex), then move to 3 which is sink in the remaining set (set excluding 4) and finally any of the remaining vertices (0, 1, 2). So how do we find this sequence of picking vertices as starting points of DFS? Unfortunately, there is no direct way for getting this sequence. However, if we do a DFS of graph and store vertices according to their finish times, we make sure that the finish time of a vertex that connects to other SCCs (other that its own SCC), will always be greater than finish time of vertices in the other SCC.

For example, in DFS of above example graph, finish time of 0 is always greater than 3 and 4 (irrespective of the sequence of vertices considered for DFS). And finish time of 3 is always greater than 4. DFS doesn't guarantee about other vertices, for example finish times of 1 and 2 may be smaller or greater than 3 and 4 depending upon the sequence of vertices considered for DFS. So to use this property, we do DFS traversal of complete graph and push every finished vertex to a stack. In stack, 3 always appears after 4, and 0 appear after both 3 and 4. In the next step, we reverse the graph.

Consider the graph of SCCs. In the reversed graph, the edges that connect two components are reversed. So the SCC {0, 1, 2} becomes sink and the SCC {4} becomes source. As discussed above, in stack, we always have 0 before 3 and 4. So if we do a DFS of the reversed graph using sequence of vertices in stack, we process vertices from sink to source (in reversed graph). That is what we wanted to achieve and that is all needed to print SCCs one by one.

![[img/sccgfg-05.webp|600]]
Graph of SCCs

```
from collections import defaultdict

class GfG:
    # Run a dfs on the original graph
    def DFS1(self, u, adj, visited, st):
        visited[u] = True
        for v in adj[u]:
            if not visited[v]:
                self.DFS1(v, adj, visited, st)
        st.append(u)

    # DFS on reversed graph to collect SCC
    def DFS2(self, u, revAdj, visited, scc):
        visited[u] = True
        scc.append(u)
        for v in revAdj[u]:
            if not visited[v]:
                self.DFS2(v, revAdj, visited, scc)

    def kosaraju(self, V, adj):
        visited = [False] * V
        st = []

        # Fill stack with finish time order
        for i in range(V):
            if not visited[i]:
                self.DFS1(i, adj, visited, st)

        # Reverse the graph
        revAdj = [[] for _ in range(V)]
        for u in range(V):
            for v in adj[u]:
                revAdj[v].append(u)

        # Process reversed graph in order of stack
        visited = [False] * V
        SCCs = []

        while st:
            u = st.pop()
            if not visited[u]:
                scc = []
                self.DFS2(u, revAdj, visited, scc)
                SCCs.append(scc)

        return SCCs

if __name__ == "__main__":
    obj = GfG()
    V = 5
    edges = [
        [1, 3], [1, 4], [2, 1], [3, 2], [4, 5]
    ]

    adj = [[] for _ in range(V + 1)]
    for u, v in edges:
        adj[u].append(v)

    SCCs = obj.kosaraju(V + 1, adj)

    print("Strongly Connected Components:")
    for i in range(len(SCCs) - 1):
        for node in SCCs[i]:
            print(node, end=" ")
        print()
```

                self.DFS2(v, revAdj, visited, scc)

**Output**

    Strongly Connected Components:
    1 2 3
    4
    5

**Time Complexity** - O(V + E)\
**Auxiliary Space** - O(V + E)

## [Expected Approach 2] Using Tarjan's Algorithm

Tarjan's Algorithm is more efficient because it finds SCCs in a single DFS pass using a stack and some additional bookkeeping:

1.  **DFS Traversal**: During the DFS, maintain an index for each node and the smallest index (low-link value) that can be reached from the node.
2.  **Stack**: Keep track of nodes currently in the recursion stack (part of the current SCC being explored).
3.  **Identifying SCCs**: When a node’s low-link value equals its index, it means we have found an SCC. Pop all nodes from the stack until we reach the current node.

Please refer **<strong>Tarjan's Algorithm**</strong> for more details
