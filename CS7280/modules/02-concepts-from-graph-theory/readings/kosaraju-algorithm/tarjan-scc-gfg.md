# Tarjan's Algorithm to find Strongly Connected Components

> Source: https://www.geeksforgeeks.org/tarjan-algorithm-find-strongly-connected-components/ — GeeksforGeeks. (Implementation shown in Python; the source page also provides C++/Java/C#/JavaScript versions.)

A directed graph is strongly connected if there is a path between all pairs of vertices. A strongly connected component (**SCC**) of a directed graph is a maximal strongly connected subgraph. For example, there are 3 SCCs in the following graph:

**Example:**

> **Input:** adj[][] = [[1], [2], [0, 3], [4], [3, 5], []]
>
>
> ![[img/tarjan-02.webp|600]]
>
>
> **Output:** [[0, 1, 2], [3, 4], [5]]\
> **Explanation:** There are 3 different Strongly Connected Components. They are {0, 1, 2}, {3, 4}, {5}.

Try It Yourself

We have discussed Kosaraju's algorithm for strongly connected components. The previously discussed algorithm requires two DFS traversals of a Graph. In this post, Tarjan's Algorithm is discussed that requires only one DFS traversal:

Tarjan Algorithm is based on the following facts: 

- DFS search produces a DFS tree/forest 
- Strongly Connected Components form subtrees of the DFS tree. 
- If we can find the head of such subtrees, we can print/store all the nodes in that subtree (including the head) and that will be one SCC. 
- There is no back edge from one SCC to another (There can be cross edges, but cross edges will not be used while processing the graph).

To find the head of an SCC, we calculate the disc and low array (as done for articulation point, bridge, and biconnected component). As discussed in the previous posts, low[u] indicates the earliest visited vertex (the vertex with minimum discovery time) that can be reached from a subtree rooted with u. A node u is head if disc[u] = low[u]

Below is an illustration of the above approach:  

![stack.webp](https://media.geeksforgeeks.org/wp-content/uploads/20260122181203158750/stack.webp)![stack.webp](https://media.geeksforgeeks.org/wp-content/uploads/20260122181203158750/stack.webp)

![stack_6-1.webp](https://media.geeksforgeeks.org/wp-content/uploads/20260123140436261142/stack_6-1.webp)![stack_6-1.webp](https://media.geeksforgeeks.org/wp-content/uploads/20260123140436261142/stack_6-1.webp)

![stack_5-1.webp](https://media.geeksforgeeks.org/wp-content/uploads/20260123140436081464/stack_5-1.webp)![stack_5-1.webp](https://media.geeksforgeeks.org/wp-content/uploads/20260123140436081464/stack_5-1.webp)

![stack_4-1.webp](https://media.geeksforgeeks.org/wp-content/uploads/20260123140435905197/stack_4-1.webp)![stack_4-1.webp](https://media.geeksforgeeks.org/wp-content/uploads/20260123140435905197/stack_4-1.webp)

![stack_3-2.webp](https://media.geeksforgeeks.org/wp-content/uploads/20260123140435728784/stack_3-2.webp)![stack_3-2.webp](https://media.geeksforgeeks.org/wp-content/uploads/20260123140435728784/stack_3-2.webp)

![stack_2-2.webp](https://media.geeksforgeeks.org/wp-content/uploads/20260123140435452870/stack_2-2.webp)![stack_2-2.webp](https://media.geeksforgeeks.org/wp-content/uploads/20260123140435452870/stack_2-2.webp)

![stack_1-1.webp](https://media.geeksforgeeks.org/wp-content/uploads/20260123140435279744/stack_1-1.webp)![stack_1-1.webp](https://media.geeksforgeeks.org/wp-content/uploads/20260123140435279744/stack_1-1.webp)

! ! ! 1 / 7

\

\

To solve the problem follow the below idea:

Strongly Connected Component relates to directed graph only, but Disc and Low values relate to both directed and undirected graph, so in the above pic we have taken an undirected graph.

In the above Figure, we have shown a graph and one of the DFS trees (There could be different DFS trees on the same graph depending on the order in which edges are traversed). In a DFS tree, continuous arrows are tree edges, and dashed arrows are back edges (DFS Tree Edges ). Disc and Low values are shown in the Figure for every node as (Disc/Low). 

> **Disc:** This is the time when a node is visited 1^st^ time while DFS traversal. For nodes A, B, C, .., and J in the DFS tree, Disc values are 1, 2, 3, .., 10. 
>
> **Low:** In the DFS tree, Tree edges take us forward, from the ancestor node to one of its descendants. For example, from node C, tree edges can take us to node G, node I, etc. Back edges take us backward, from a descendant node to one of its ancestors. 

For example: From node G, the Back edges take us to E or C. If we look at both the Tree and Back edges together, then we can see that if we start traversal from one node, we may go down the tree via Tree edges and then go up via back edges. 

For example, from node E, we can go down to G and then go up to C. Similarly from E, we can go down to I or J and then go up to F. "Low" value of a node tells the topmost reachable ancestor (with minimum possible Disc value) via the subtree of that node. So for any node, a Low value is equal to its Disc value anyway (A node is the ancestor of itself). Then we look into its subtree and see if there is any node that can take us to any of its ancestors. 

If there are multiple back edges in the subtree that take us to different ancestors, then we take the one with the minimum Disc value (i.e. the topmost one). If we look at node F, it has two subtrees. Subtree with node G takes us to E and C. The other subtree takes us back to F only. Here topmost ancestor is C where F can reach and so the Low value of F is 3 (The Disc value of C). 

Based on the above discussion, it should be clear that the Low values of B, C, and D are 1 (As A is the topmost node where B, C, and D can reach). In the same way, the Low values of E, F, and G are 3, and the Low values of H, I, and J are 6.\
For any node u, when DFS starts, Low will be set to its Disc 1^st^

Then later on DFS will be performed on each of its children v one by one, Low value of u can change in two cases: 

> - **Case1 (Tree Edge):** If node v is not visited already, then after the DFS of v is complete, a minimum of low[u] and low[v] will be updated to low[u]. \
>   low[u] = min(low[u], low[v]); 
> - **Case 2 (Back Edge):** When child v is already visited, then a minimum of low[u] and Disc[v] will be updated to low[u]. \
>   low[u] = min(low[u], disc[v]); 

In case two, can we take low[v] instead of the disc[v] ?? The answer is **NO**. If you can think why the answer is **NO**, you probably understood the Low and Disc concept.

![[img/tarjan-01.jpg|600]]

Same Low and Disc values help to solve other graph problems like articulation point, bridge, and biconnected component. To track the subtree rooted at the head, we can use a stack (keep pushing the node while visiting). When a head node is found, pop all nodes from the stack till you get the head out of the stack. To make sure, we don't consider cross edges, when we reach a node that is already visited, we should process the visited node only if it is present in the stack, or else ignore the node.  

Below is the implementation of Tarjan's algorithm to print all SCCs. 

```
# A recursive DFS based function used by getSCCs()
# u        -> The vertex to be visited next
# disc[]   -> Stores discovery times of visited vertices
# low[]    -> Earliest visited vertex that can be reached
#             from subtree rooted with current vertex
# st       -> Stack to store all active DFS vertices
# inSt[]   -> Boolean array to check whether a node is in stack
# timer    -> Global time counter for discovery times
# allSCCs  -> Stores all strongly connected components
def findSCC(u, adj, disc, low, inSt, st, timer, allSCCs):

    # Initialize discovery time and low value
    timer[0] += 1
    disc[u] = low[u] = timer[0]

    # Push current vertex to stack and mark it as in stack
    st.append(u)
    inSt[u] = True

    # Go through all vertices adjacent to this
    for v in adj[u]:

        # If v is not visited yet, then recur for it
        # Case 1: Tree edge
        if disc[v] == -1:

            findSCC(v, adj, disc, low, inSt, st, timer, allSCCs)

            # Check if the subtree rooted with v has a
            # connection to one of the ancestors of u
            low[u] = min(low[u], low[v])

        # Update low value of u only if v is still in stack
        # Case 2: Back edge (not cross edge)
        elif inSt[v]:
            low[u] = min(low[u], disc[v])

    # If u is head node of SCC, pop the stack and store the SCC
    if low[u] == disc[u]:

        scc = []

        # Pop all vertices from stack till u is found
        while True:

            x = st.pop()
            inSt[x] = False
            scc.append(x)

            if x == u:
                break

        # Store one strongly connected component
        allSCCs.append(scc)

# The function to do DFS traversal.
# It uses findSCC() to find all strongly connected components
def getSCCs(adj):

    n = len(adj)
    disc = [-1] * n
    low = [-1] * n
    inSt = [False] * n

    st = []
    timer = [0]
    allSCCs = []

    # Call the recursive helper function to find SCCs
    # in DFS tree with vertex i
    for i in range(n):

        if disc[i] == -1:
            findSCC(i, adj, disc, low, inSt, st, timer, allSCCs)

    return allSCCs

if __name__ == "__main__":

    adj = [[] for _ in range(6)]

    # Graph construction
    adj[0].append(1)
    adj[1].append(2)
    adj[2].append(0)
    adj[2].append(3)
    adj[3].append(4)
    adj[4].append(3)
    adj[4].append(5)

    sccs = getSCCs(adj)

    print("Strongly Connected Components:")
    for scc in sccs:
        print(*scc)
```

            findSCC(v, adj, disc, low, inSt, st, timer, allSCCs)

**Output**

    Strongly Connected Components:
    5
    4 3
    2 1 0

**Time Complexity:** The above algorithm mainly calls DFS, DFS takes O(V+E) for a graph represented using an adjacency list. \
**Auxiliary Space:** O(V)
