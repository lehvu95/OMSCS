# Lesson 14 — Knowledge Check

> Source: Canvas — CS-7280-O01, OAN (Summer 2026)

Ungraded knowledge check. See also [[lesson14-knowledge-check.pdf]].

---

### Q1 — Multiple answer (1 point)

In the node embedding problem, we compute a $d$-dimensional vector for each node of the network. Which of the following statements is/are true about the magnitude of $d$:

- [ ] $d$ should be at least equal to the number of nodes in the network.
- [ ] The higher $d$ is, the closer the similarity of two node embeddings to the network similarity of the corresponding nodes.
- [ ] Any value of $d$ will produce good node embeddings but higher values of $d$ give embeddings with higher inductive power.
- [ ] If $d$ is not high enough, it may be that two pairs of nodes have almost the same dot product even though they are not equally similar.

---

### Q2 — Multiple answer (1 point)

Consider the architecture of Graph Neural Networks (GNNs). Which of the following statements is/are true?

- [ ] The embedding of each node $v$ at a layer $k$ ($k>0$) is a linear function of the embeddings of node $v$'s neighbors (including itself) at layer $(k-1)$.
- [ ] If two nodes $u$ and $v$ have the same set of neighbors, then they will have the same embedding vectors at each layer.
- [ ] The dimensionality of the matrices $W_k$ and $B_k$ is the dimensionality at layer $k$.
- [ ] If we do not have any input node features, we can simply set the initial embedding of each node $v$ to zero (i.e., $h_v^0 = 0$ for all nodes $v$).

---

### Q3 — Multiple answer (1 point)

Consider the cross-entropy loss function used to train GNNs for binary node classification. Which of the following statements is/are correct?

- [ ] The loss function is close to 0 whenever the model predicts correctly the label of a node.
- [ ] The loss function is equal to 1 whenever the model predicts incorrectly the label of a node.
- [ ] The loss function assumes that the activation function $\sigma$ varies between 0 and 1.
- [ ] The loss function assumes that the activation function $\sigma$ is equal to either 0 or 1.

---

### Q4 — Multiple answer (1 point)

Consider the GNN we reviewed in the polypharmacy application. Which of the following statements is/are true about the "decoder" part of the network?

- [ ] It predicts whether an edge of a given type exists between any two given nodes
- [ ] It predicts whether an edge exists between two given drug nodes
- [ ] It predicts whether an edge of a given type exists between two given drug nodes
- [ ] The edge predictions use the same trainable parameters for any type of edge

---

### Q5 — Multiple answer (1 point)

Which of the following statement(s) is/are true about the DeepWalk method?

- [ ] Ordering the nodes encountered during the random walk is important because earlier nodes receive a larger weight in the softmax ratio.
- [ ] DeepWalk embeddings can capture global information better than embeddings based on cosine similarity.
- [ ] If a node is encountered more than once in a random walk, DeepWalk filters out such duplicates to avoid bias.
- [ ] DeepWalk prefers long random walks so that even two distinct nodes co-occur in the same walk.

---

### Q6 — Multiple choice (1 point)

The section "Deep Embeddings and Graph Neural Networks" of this Lesson described a way to compute node embeddings considering the given node features. Suppose we are also given some edge features (e.g., the strength of the connection $e_{u,v}$ between nodes $u$ and $v$). What can we do to consider both node and edge attributes in the computation of node embeddings?

- [ ] The approach described in this lecture already covers edge features
- [ ] We can use $\mathbf{h}_v^k = \sigma\left(\frac{1}{|N(v)|} \sum_{u \in N(v)} \phi(\mathbf{e}_{u,v})\mathbf{h}_u^{k-1} + \mathbf{B}_k \mathbf{h}_v^{k-1}\right)$ where $\phi(\mathbf{e}_{u,v})$ is a trainable neural network that maps $\mathbf{e}_{u,v}$ to $\mathcal{R}^{d_k \times d_{k-1}}$.
- [ ] We can calculate a scalar feature for each edge by adding the elements of the corresponding feature vector for that edge.
- [ ] It is not possible to consider edge features in the computation of node embeddings.
