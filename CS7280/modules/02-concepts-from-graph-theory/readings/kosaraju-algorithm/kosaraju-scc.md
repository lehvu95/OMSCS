> Source: https://www.topcoder.com/thrive/articles/kosarajus-algorithm-for-strongly-connected-components — TopCoder Thrive (Nikhil Kumar Singh).

# Kosaraju's Algorithm for Strongly Connected Components

If we can reach every vertex of a component from every other vertex in that component then it is called a Strongly Connected Component (SCC). Single node is always a SCC.

The graph below is a basic example of SCC, as it has four SCCs each contained in its own shape.

![[img/tcksj-01.png|600]]

To find SCCs we have two algorithms, **Tarjan’s and Kosaraju’s algorithms.** In this article, we are going to cover Kosaraju’s algorithm. To learn more about **Tarjan’s algorithm** check out [this article](https://www.topcoder.com/thrive/articles/tarjans-algorithm-for-strongly-connected-components).

### Brute Force Method

We can use the Floyd Warshall algorithm to compute the distance between every two vertices, then check if the distance between any two pairs is infinity. This means both are unreachable, except for the fact that it might be a self-loop. But, it has a time complexity of about O(V3), which we cannot afford in most of the scenarios.

### Kosaraju’s Algorithm

Before we deep dive into Kasaraju’s algorithm, we must take a note on reversing all the edges of a graph. The type of graph won’t change, as a SCC will still remain a SCC.\
Only the direction between components is reversed. This property is used in our article to detect SCCs.

![[img/tcksj-02.png|600]]

The transpose graph property is why Kosaraju’s algorithm works successfully to search SCCs.

Below you will see that if we start DFS on the original graph from any node in SCC1 we will be able to reach all the nodes in all the three components, as all are strongly connected components and there is an outgoing edge from the first node to SCCs.\
But, if we try doing DFS on the transposed graph from any node in SCC1 we will only be able to reach all nodes in the SCC1 component as there is no outgoing edge from one SCC to another. So, to reach the other SCC we have to make a manual jump. When we do this we can deduce that the last component was a strongly connected component. Now we start our counter and do the above steps again to get the remaining SCCs.

![[img/tcksj-03.png|600]]

**PSEUDOCODE:**

- Perform DFS traversal of the graph. Push node to stack before returning.

- Find the transpose graph by reversing the edges.

- Pop nodes one by one from the stack and again to DFS on the modified graph.

Let’s show an example to support our algorithm:

![[img/tcksj-04.png|600]]

We will begin DFS at 0 on the above graph and traverse every outgoing edge from each node that is unvisited. For visiting information we will make a visited array, and we should also maintain a stack to store the nodes in the order of which we exhausted their outgoing edges. Now we will see the result:

![[img/tcksj-05.png|600]]

Now we pop the stack one by one and do DFS on the modified/traversed graph while popping nodes. At the end of each successful DFS we will have an SCC.

Now go ahead and perform this. For the sake of the article I won’t be illustrating it (might take too many pages), I will just show the final result. Here you’ll see each SCC colored differently. We will do the steps the same as the previous one, but the next node to traverse will be given by stack. Ignore those stack elements which have already been considered in previous SCCs.

![[img/tcksj-06.png|600]]

### Code Implementation:

```
1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
24
25
26
27
28
29
30
31
32
33
34
35
36
37
38
39
40
41
42
43
44
45
46
47
48
49
50
51
52
53
54
55
56
57
58
59
60
61
62
63
64
65
66
67
68
69
70
71
72
73
#include <bits/stdc++.h>

#define MAX_N 20001
#define ll long long int
using namespace std;
int n, m;

struct Node {
  vector < int > adj;
  vector < int > rev_adj;
};

Node g[MAX_N];

stack < int > S;
bool visited[MAX_N];

int component[MAX_N];
vector < int > components[MAX_N];
int numComponents;

void dfs_1(int x) {
  visited[x] = true;
  for (int i = 0; i < g[x].adj.size(); i++) {
    if (!visited[g[x].adj[i]]) dfs_1(g[x].adj[i]);
  }
  S.push(x);
}

void dfs_2(int x) {
  printf("%d ", x);
  component[x] = numComponents;
  components[numComponents].push_back(x);
  visited[x] = true;
  for (int i = 0; i < g[x].rev_adj.size(); i++) {
    if (!visited[g[x].rev_adj[i]]) dfs_2(g[x].rev_adj[i]);
  }
}

void Kosaraju() {
  for (int i = 0; i < n; i++)
    if (!visited[i]) dfs_1(i);

  for (int i = 0; i < n; i++)
    visited[i] = false;

  while (!S.empty()) {
    int v = S.top();
    S.pop();
    if (!visited[v]) {
      printf("Component %d: ", numComponents);
      dfs_2(v);
      numComponents++;
      printf("\n");
    }
  }
}

int main() {

  cin >> n >> m;
  int a, b;
  while (m--) {
    cin >> a >> b;
    g[a].adj.push_back(b);
    g[b].rev_adj.push_back(a);
  }

  Kosaraju();
  printf("Total number of components: %d\n", numComponents);

  return 0;
}
```

**Input:**

```
1
2
3
4
5
6
7
8
9
10
11
8 10
0 1
1 2
2 0
2 3
3 4
4 5
5 6
6 7
4 7
6 4
```

**Output:**

```
1
2
3
4
5
Component 0: 0 2 1
Component 1: 3
Component 2: 4 6 5
Component 3: 7
Total number of components: 4
```

Kosaraju’s algorithm aims to find all strongly connected components (SCCs) of a given input graph. It is less effective than Tarjan’s, as here we have two different types of DFS calling, but it is more intuitive.

Complexity: **O(V + E)**

!

5

!

0

 Chat on Discord

