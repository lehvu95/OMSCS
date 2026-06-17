# Lesson Fourteen — Machine Learning in Network Science

> Source: Canvas — CS-7280-O01, OAN (Summer 2026)

## 00 — Lesson Overview

Throughout the lecture, we are giving you some *"food for thought"* — these are questions we suggest you think about as you go through this lesson. You do not need to submit solutions.

### Learning Objectives

Students will:

- Understand what "representation learning" means in the context of networks
- Study different methods to compute node and link embeddings
- Apply deep learning approaches in the context of graphs (graph neural networks) — and explore an application (side-effects of polypharmacy)
- Gain a high-level understanding of state-of-the-art research areas in network science, including temporal networks and interdependent networks

### Required and Recommended Reading

**Required Reading**

- ["Representation learning on graphs: Methods and applications"](https://arxiv.org/abs/1709.05584), by W. L. Hamilton et al., 2017 — see [[representation-learning-on-graphs.pdf|local copy]].

**Recommended Reading**

- ["Deep learning on graphs: A survey"](https://ieeexplore.ieee.org/abstract/document/9039675), by Z. Zhang et al., 2020 — see [[deep-learning-on-graphs-survey.pdf|local copy]].
- ["Temporal networks"](https://www.sciencedirect.com/science/article/pii/S0370157312000841), by P. Holme and Z. Saramäki, 2012 — see [[temporal-networks-holme-saramaki.pdf|local copy]].
- ["The structure and dynamics of multilayer networks"](https://www.sciencedirect.com/science/article/pii/S0370157314002105), by S. Boccaletti et al., 2014 — see [[structure-and-dynamics-of-multilayer-networks.pdf|local copy]].

### Assignments

- L14: Knowledge Check
- L14: Quiz

### Video: Introduction to Machine Learning in Network Science

[[sections/00-lesson-overview.mp4]]

Video URL: https://mediaspace.gatech.edu/media/t/1_uzy8bmgv

| Text |
|------|
| The previous lessons focused on the overlap between network science and statistics. In  |
| this lesson we focus on the overlap between network science and machine learning. This is  |
| a research area of growing interest, and there is rapid progress both in theoretical  |
| questions and in many applications. Our focus will be on two topics, the first is network  |
| representation learning. We will discuss how to create node and graph embeddings, and how  |
| to use them to answer various questions related to link prediction or node  |
| classification. The second topic relates to graph neural networks. Here we will rely on  |
| the expressive power of deep neural networks to learn graph models from data. A key  |
| question is how to represent the topology of a network using the parameters of neural  |
| network hidden units. We will also see an application of graph neural networks focusing  |
| on the effect of polypharmacy. The side effects of receiving different combinations of  |
| medical drugs, and how to predict negative side effects that have not been observed  |
| before. We will close this lesson with an overview of some other advanced topics, that we  |
| will not have the chance to cover in detail in this course. Temporal networks,  |
| interdependent networks, and graph signal processing. |

## 01 — Embedding Nodes in a Low-dimensional Space

Machine Learning (ML) is a mature discipline with powerful methods to solve classification, clustering, regression and many other problems in data science. Most ML methods however require a **vector representation** of the inputs. This is easy with structured data that already come as vectors or matrices, and even for images (a vector of pixel intensities). How can we represent a graph with a vector, when a graph can have an arbitrary structure?

One option would be to represent each node $v$ with an $N$-dimensional binary vector ($N$ = number of nodes): element $i$ is one if node $i$ is a neighbor of $v$ and zero otherwise. But that representation is high-dimensional for large networks, and the sampling efficiency of most ML algorithms is determined by that dimensionality. So we want graph-representation methods that map each node to a $d$-dimensional vector with $d \ll N$. The $d$-dimensional vector for a node $u$ is its **"embedding"** $f(u)$.

![[img/01-node-embedding-1.png|500]]

> Images from Jure Leskovec, "Representation Learning on Networks" tutorial, WWW 2018.

Consider Zachary's karate club network (Lesson-7), and suppose we want to represent each node with a two-dimensional vector. We would map any two nodes that are "close to each other" in network distance (directly connected, or with many common neighbors) to two nearby points in the plane — and nodes with large network distance to distant points. The figure shows an embedding of the karate-club nodes using the **DeepWalk** algorithm (covered later).

![[img/01-node-embedding-2.png|500]]

> Image from: Perozzi et al. 2014. *DeepWalk: Online Learning of Social Representations*, KDD.

Why base node embeddings on network distance? The network distance between two nodes is usually related to their similarity — e.g., in a social network, individuals with strong ties and many common friends tend to have similar interests. Many ML methods (K-nearest neighbors, Support Vector Machines) assume that the similarity between two inputs is reflected by the distance between their embeddings.

![[img/01-node-embedding-3.png|500]]

For example, to classify "politically unlabeled" people (Democrat, Republican, Independent), embeddings based on network connectedness make sense: individuals in the same social groups map to nearby embeddings. For **community detection**, if the embeddings are based on network distance, we can apply any ML clustering algorithm (such as K-means) to find clusters of nearby points in the embedding space.

**Food For Thought**

The Karate club embeddings are deliberately shown in low-resolution so the node labels are not clear. Can you identify at least five of the nodes from their embeddings?

## 02 — Shallow Encodings and Similarity Metrics

In this page we discuss some simple approaches to compute node embeddings. They are "shallow" because computing them does not require training a deep neural network.

With $n$ nodes and embedding dimensionality $d$, the node embeddings can be encoded in a $d \times n$ matrix $\mathbf{Z}$. If $\mathbf{v}$ is an $n \times 1$ "one-hot" vector (all zeros except a one at node $v$), then the embedding of node $v$ is:

$$\mbox{ENC}(v)=\mathbf{Z}\,\mathbf{v}$$

which simply extracts the column of $\mathbf{Z}$ corresponding to node $v$.

![[img/02-shallow-encoding-1.png|500]]

> Images from Jure Leskovec, "Representation Learning on Networks" tutorial, WWW 2018.

Let us compute $\mathbf{Z}$ based on different notions of "node similarity". The **simplest** approach: two nodes are similar only if **directly connected** (with similarity equal to the edge weight if weighted). If $\mathbf{A}$ is the (possibly weighted) $n\times n$ adjacency matrix, we compute $\mathbf{Z}$ so that the dot-product of the embeddings $\mathbf{z}_u$ and $\mathbf{z}_v$ equals $\mathbf{A}_{u,v}$. One way is to minimize the loss function via a numerical method such as Stochastic Gradient Descent:

$$\mathcal{L}=\sum_{(u,v)\in V\times V} \|\mathbf{z}_u^T \mathbf{z}_v-\mathbf{A}_{u,v}\|$$

A drawback: two nodes are considered "not similar" if not directly connected, even with many common neighbors.

![[img/02-shallow-encoding-2.png|500]]

A more general approach considers a node $v$ "similar" not only to its direct neighbors but to any node at most $k$-hops away (for small $k$, say 2 or 3). We then use the same loss but replace $\mathbf{A}$ with a $k$-hop adjacency matrix $\mathbf{A}_k$, or use the first $k$ powers of $\mathbf{A}$ (recall from Lesson-2 that $\mathbf{A}^k$ gives the number of $k$-hop paths between nodes).

![[img/02-shallow-encoding-3.png|500]]

Another approach considers the **overlap between the network neighborhoods** of two nodes. Recall the node-similarity metric from Lesson-7:

$$S_{i,j} = \frac{N_{i,j}+A_{i,j}}{\min\{k_i,k_j\}}$$

where $N_{i,j}$ is the number of common neighbors of $i$ and $j$, $A_{i,j}$ is the adjacency element (1 if connected), and $k_i$ is the degree of node $i$. Note $S_{i,j}=1$ if the two nodes are connected and every neighbor of the lower-degree node is also a neighbor of the other; $S_{i,j}=0$ if not connected and with no common neighbor. Given such a metric, the embeddings are computed from:

$$\mathcal{L}=\sum_{(u,v)\in V\times V} \|\mathbf{z}_u^T \mathbf{z}_v-\mathbf{S}_{u,v}\|$$

All three approaches share two drawbacks: they are computationally expensive (the loss considers every node pair, even weakly similar ones — addressable with regularization), and they require a separate embedding vector per node (so the number of parameters scales with network size). Ideally we want a scheme whose parameter count is constant or sub-linear in network size — covered later.

**Food For Thought**

1) The loss functions rely on the dot-product of embedding vectors. How would you modify them to rely instead on the L2-distance of embedding vectors?

2) Which method would you prefer if the network is weighted and directed?

## 03 — Random-walk Encodings and Node2vec

The previous embedding methods are deterministic. More recent methods rely on **stochastic** notions of "neighborhood overlap". In particular, **DeepWalk** (a misnomer — it does not use deep learning) and **node2vec** are the most popular. Both construct node embeddings based on **random walks**: two nodes $u$ and $v$ have similar embeddings ($\mathbf{z}_u \approx \mathbf{z}_v$) if they tend to co-occur on short random walks over the graph.

![[img/03-node2vec-1.png|500]]

> Images from Jure Leskovec, "Representation Learning on Networks" tutorial, WWW 2018.

Suppose $P_R(v\mid u)$ is the probability of visiting node $v$ on random walks of length $T$ starting at node $u$ ($T$ typically between 2 and 10). If that probability is high, the two nodes are "close" and should have similar embeddings. We parameterize $P_R(v\mid \mathbf{z}_u)$ using a "softmax" ratio of the node embeddings:

$$\frac{e^{\mathbf{z}^T_u \mathbf{z}_v}}{\sum_{n\in V}e^{\mathbf{z}^T_u \mathbf{z}_n}} \approx P_R(v\mid\mathbf{z}_u)$$

We then compute the embeddings by minimizing the **cross-entropy loss**:

$$\mathcal{L} = \sum_{u \in V}\sum_{v \in N_R(u)} -\log P(v\mid\mathbf{z}_u)$$

where $N_R(u)$ is the multi-set of nodes in the ensemble of random walks of length $T$ starting from $u$ (a multi-set because nodes can be visited multiple times). The goal is to adjust the embeddings so that $P_R(v\mid\mathbf{z}_u)$ is close to 1 when $v \in N_R(u)$ and close to 0 otherwise.

Algorithmically: run short random walks of length $T$ from each node $u$; compute $N_R(u)$; optimize the embeddings $\mathbf{z}_v$ based on the loss. Methods use various approximations — e.g., node2vec uses a set of **"negative samples"** to approximate the softmax denominator so the summation need not consider all node pairs.

![[img/03-node2vec-2.png|500]]

Another difference is that node2vec introduces two parameters, $p$ and $q$, that bias the random walk. Suppose a walk started at $u$ and is now at $w$. The neighbors of $w$ can be closer to $u$ (s1), farther from $u$ (s3), or the same distance (s2). The two parameters that control where to go next are:

- $p$ — the **return parameter** (BFS-like walk for a low value of $p$)
- $q$ — the **"walk away" parameter** (DFS-like walk for a low value of $q$)

![[img/03-node2vec-3.png|500]]

> Images from Jure Leskovec, "Representation Learning on Networks" tutorial, WWW 2018.

Random-walk approaches are more **expressive** than the deterministic methods (the notion of similarity is stochastic and incorporates both local and distant neighbors) and more **efficient** (training only considers node pairs that co-occur on short random walks, not all possible pairs).

**Food For Thought**

Suppose we do not use the softmax ratio to parameterize $P_R(v\mid\mathbf{z}_u)$. Can you think of another way to parameterize these probabilities as a function of the node embedding vectors?

## 04 — Applications of Node Embeddings

> Images from Jure Leskovec, "Representation Learning on Networks" tutorial, WWW 2018.

![[img/04-embedding-applications-1.png|500]]

How can we use node embeddings to answer questions about the original network? Classical ML tasks — classification, clustering, regression, anomaly detection, feature learning — all have network counterparts:

- **Node classification.** ML classifiers (neural nets, decision trees, SVMs) can classify network nodes by type (male/female, human/bot, political affiliation). We need training pairs $(\mathbf{z}_v, c_v)$ — the embedding and the class of node $v$ — for at least some nodes.
- **Link prediction.** Network data are noisy (false positive/negative edges). Given embeddings computed from a noisy adjacency estimate, we can train a binary classifier to predict whether two nodes are connected, using a training set of confidently connected / not-connected pairs.
- **Community detection.** Using embeddings that reflect network distance, we can apply any of the hundreds of ML clustering algorithms — a large "toolbox" — to find clusters of nearby points.
- **Visualization.** With two-dimensional embeddings, we can plot the nodes in the Euclidean plane, with shorter network distance giving more similar embeddings.

As the next page shows, shallow embeddings have fundamental limitations, which motivates the use of deep neural networks to represent graphs.

## 05 — Deep Embeddings and Graph Neural Networks

Deep Learning (neural networks with several layers of hidden units) gives models that can learn complex nonlinear and hierarchical input-output functions. The embedding methods so far are "shallow". Shallow embeddings have several problems:

- The model parameters include a **different embedding vector for each node** — an issue for huge graphs. Ideally we want to compute any node's embedding with a single model, sharing parameters across nodes.
- They have **no inductive capability** — they cannot generalize beyond the training graph to nodes that join later (dynamic graphs) or nodes that are not visible.
- They are based strictly on connectivity (the adjacency matrix) and **cannot model arbitrary node attributes** (gender, age, salary, etc.).

We now present **Graph Neural Networks (GNNs)** (other methods include Graph Convolutional Networks and Graph Recurrent Neural Networks). Given a graph $G$ with node set $V$ ($n$ nodes), adjacency matrix $\mathbf{A}$, and an $m$-dimensional attribute vector $\mathbf{x}_v$ per node, a GNN computes an embedding vector for each node at each layer. Let $h_v^k$ be the embedding of node $v$ at layer $k$. At the input layer, $h_v^0=\mathbf{x}_v$ (the node attributes).

![[img/05-gnn-1.png|500]]

At hidden layer $k>0$, the embedding $h_v^k$ depends on both the previous-layer embedding of the same node $h_v^{k-1}$ and the previous-layer embeddings $h_u^{k-1}$ of every neighbor $u$ of $v$. Specifically, with $N(v)$ the set of neighbors of $v$, $h_v^k$ depends on the **average** of $h_u^{k-1}$ over $u \in N(v)$ — the contribution of the local neighborhood.

![[img/05-gnn-2.png|500]]

> All images on this page are from Jure Leskovec, "Representation Learning on Networks" tutorial, WWW 2018.

For example, the embedding of node A at layer 2 depends on the layer-1 embeddings of A's neighbors B, C, D; node B's layer-1 embedding depends on the layer-0 embeddings of its neighbors A and C; and so on. In practice all these per-node networks are integrated into one model.

![[img/05-gnn-3.png|500]]

What is the mathematical form? As in most neural networks, a hidden unit with input vector $\mathbf{x}$ outputs a nonlinear activation $\sigma()$ of the weighted sum of inputs:

$$\sigma\left(\sum^d_{i=0}w_i x_i\right)$$

where $\mathbf{w}$ are the learned weights (with a bias term $w_0$ for $x_0=1$). The activation $\sigma()$ could be a sigmoid, but most models now use ReLU. The layer-$k$ weights are the matrices $\mathbf{W}_k$ (applied to the average neighbor embedding from the previous layer) and $\mathbf{B}_k$ (applied to the node's own previous-layer embedding). The complete equation the GNN computes for each node $v$ at each layer $k$ is:

$$h_v^k = \sigma\left(\mathbf{W}_k \sum_{u\in N(v)} \frac{h_u^{k-1}}{|N(v)|} + \mathbf{B}_k\, h_v^{k-1}\right), \qquad h_v^0 = \mathbf{x}_v$$

![[img/05-gnn-4.png|500]]

The model captures the graph topology through each node's local neighborhood $N(v)$. At layer 1, the model only "knows" the direct neighbors; at layer 2, also the neighbors of neighbors; a sufficiently deep network (large $k$) can learn subtle structural properties within a $k$-hop neighborhood. Crucially, the parameters $\mathbf{W}_k$ and $\mathbf{B}_k$ are **shared across nodes** at layer $k$ — so we do not learn different parameters per node. This gives two benefits: a large reduction in model complexity, and **inductive capability** (the matrices can be applied even to nodes not in the training set).

**Food For Thought**

a) There is a "hidden assumption" behind using the same parameters for all nodes at each layer. State that assumption precisely.

b) What is the rationale for NOT using the same shared parameters at every layer?

## 06 — GNN Training and Decoders

Let us see how to train a GNN. For simplicity, consider a binary node-classification task: distinguish whether each node of an online social network is human (class 0) or bot (class 1). Other tasks (clustering, link prediction, multi-class) are similar with minor changes to the loss.

Suppose the network has $K$ hidden layers. The final embedding of each node $v$ is $\mathbf{z}_v = h_v^K$. We also design the **"decoder"**, which maps $\mathbf{z}_v$ to the class of $v$. The simplest decoder is a "softmax" operator with parameters $\mathbf{D}$ (a vector of the same dimensionality as the embedding), with output:

$$\sigma\left(\mathbf{z}_v^T \mathbf{D}\right)$$

If the output is closer to 0 we predict class 0; closer to 1, class 1.

![[img/06-gnn-training-1.png|500]]

> Images from Jure Leskovec, "Representation Learning on Networks" tutorial, WWW 2018.

To compute all parameters — the encoder ($\mathbf{W}_k, \mathbf{B}_k$ for $k=1,\dots,K$) and the decoder ($\mathbf{D}$) — suppose we are given the actual class $y_v \in \{0,1\}$ for a set $V'$ of nodes. We minimize the **cross-entropy loss**:

$$\mathcal{L}=-\sum_{v \in V'} \left[y_v \log\left(\sigma(\mathbf{z}_v^T \mathbf{D})\right) + (1-y_v) \log\left(1-\sigma(\mathbf{z}_v^T \mathbf{D})\right)\right]$$

When the softmax output is close to the actual class ($y_v \approx \sigma(\mathbf{z}_v^T \mathbf{D})$), node $v$ contributes almost 0 to the loss; when the model predicts the wrong class ($y_v + \sigma(\mathbf{z}_v^T \mathbf{D}) \approx 1$), it contributes significantly. The optimization is non-convex, so training relies on numerical methods such as Stochastic Gradient Descent (SGD).

![[img/06-gnn-training-2.png|500]]

After training, we can classify any node, including those without training data. We can also compute embeddings (and classify) for nodes **not present in the original network**: if the GNN was trained on the grey portion of a graph and a node $u$ joins later, we can use the same GNN without retraining to embed and classify $u$ — as long as the new nodes follow the same structural properties. Similarly, a GNN can **generalize to entirely new graphs** with the same structural properties — e.g., trained on protein-protein interaction networks of closely related species (*Salmonella typhi*, *Salmonella typhimurium*) and applied to predict protein properties in a novel *Salmonella* species.

**Food For Thought**

a) How would you modify the loss function for multiple classes (multinomial classification)?

b) If the task is to predict links between nodes rather than classify nodes, how would you train the GNN given a training graph?

## 07 — Application: Polypharmacy

This section presents a research application of graph neural networks: predicting the side effects of **polypharmacy** (the simultaneous use of multiple drugs) by modeling drug–drug and drug–protein interactions as a multimodal graph and learning with a graph convolutional network. The application's research publication (Zitnik et al., *Decagon*) is provided as a local copy: see [[modeling-polypharmacy-side-effects-gcn.pdf|local copy]].

### Video: Application: Polypharmacy

[[sections/07-application-polypharmacy.mp4]]

Video URL: https://mediaspace.gatech.edu/media/t/1_vi6ubgbl

| Text |
|------|
| Polypharmacy means that a patient receives multiple medications at the same time. It is  |
| common with complex diseases and coexisting conditions, but it has high risk of side  |
| effects due to drug interactions. 15% of the US population is affected by polypharmacy  |
| and the annual costs exceed 177 billion. It is also difficult to identify manually  |
| because it is rare. It occurs only in a small subset of patients and it is not observed  |
| in clinical testing. Here is an example of how to model polypharmacy with a network. The  |
| network is multimodal because there are different types of nodes and edges. The green  |
| nodes represent drugs, while the orange nodes represent genes and the corresponding  |
| proteins that are encoded by these genes. The edge is between genes represent  |
| protein-protein interactions and nodes between a gene and the drug means that that drug  |
| targets the corresponding protein. And the edges between two drugs represent interactions  |
| between these two drugs. Those edges are labeled as you see here with r_1, r_2, and so  |
| on. The label of such an edge represents the side effect that would be caused if those  |
| two medications are taken together. Such networks can be constructed based on genomic  |
| data, patient population data, and known side effects of different drug combinations. If  |
| we have any additional information about proteins or drugs, it can't be included in the  |
| model as different node features. In this visualization, the neighbors of the antibiotic  |
| called ciprofloxacin node C indicate that this drug targets four proteins and it  |
| interacts with three other drugs. Ciprofloxacin, which is node C, taken together with  |
| doxycycline, which is node D, or with simvastatin node S, increases the risk of  |
| bradycardia. Bradycardia side effect is represented in this graph with the edges that are  |
| labeled with r_2. The combination of ciprofloxacin with mupirocin is the node M, on the  |
| other hand, increases the risk of gastrointestinal bleeding, which is represented by the  |
| edge labeled r_1. The goal of this graph neural network model called decagon, is to  |
| predict unknown edges between drugs. Decagon predicts associations basically between  |
| pairs of drugs with a goal of identifying side effects that cannot be attributed to  |
| either individual drug in the pair. Here is an example of the neural networks encoder.  |
| What you see at the right is the per layer update for a single graph node, the node  |
| representing ciprofloxacin node C, the hidden state activations from neighboring nodes  |
| are gathered and then transformed for each relation tie specifically. The top-left  |
| rectangle shows the contribution of the r_1 edge on the activation of node C at layer k  |
| plus 1. That activation depends on the activation of node C at the previous layer, layer  |
| k, as well as the activation of node M at layer k. Similarly, the middle rectangle at the  |
| right shows the contribution of the r_2 edges on the activation of node C, the bottom  |
| rectangle shows the contribution of the four target genes on the activation of node C.  |
| These three representations are accumulated in a normalized sum and then pass through a  |
| non-linear activation function, such as a ReLu to produce the hidden state of node C at  |
| layer k plus 1. Sets per node updates are computed in parallel across the whole network  |
| with shared parameters for each type of edge. Let us now see how Decagon can predict the  |
| existence of unknown side effects for a pair of drugs. This is the decoder part of the  |
| Decagon network. Suppose for example, that we want to examine if two drugs, C and S have  |
| the side effect represented by each relation type r_1, r_2, all the way to r_n. For each  |
| of these relations, the Decagon decoder takes the pair of embeddings for nodes C and S,  |
| and it produces a score for every potential relation edge between these two nodes through  |
| a fully-connected neural layer that is unique for each relation. This type of inductive  |
| inference is possible because even though the Decagon neural network is different for  |
| each node, all of these networks say the same trainable parameters for each type of edge.  |
| So the trainable parameters that refer to the relation r_2, which is bradycardia are the  |
| same independent of whether those parameters are used for the side effects of drug C or S  |
| or D. |

## 08 — Advanced Topics: Deep Generative Models for Graphs

> Source: "Machine Learning with Graphs" — Jure Leskovec, Stanford CS224W.

We have studied several network generation models (mostly Lesson-12): models with one or two parameters (Erdős-Rényi, preferential attachment) and models with more parameters that create modular or hierarchical structure (stochastic block models). All of these are based on **explicit, prescribed** assumptions about the desired structure (e.g., we choose preferential attachment to get a power-law degree distribution of a certain exponent).

What if we want to generate networks with similar structure to one or more given real networks — **without an explicit structural characterization**? For example, given a portion of the Facebook friendship graph, create synthetic networks with the same structural properties, even though we may not be able to list (or even know) all those properties.

![[img/08-deep-generative-models-1.png|550]]

The goal is to use one or more given graphs (the data) to learn a high-dimensional **joint distribution** (the model) giving the probability that any two nodes are connected, given the connectivity among all other nodes. We can then generate many synthetic networks of arbitrary size sharing the same structural properties. The main challenges are:

- The model should generate graphs of **arbitrary size and density** — difficult if the data only cover networks of one size/density.
- It must handle **graph isomorphism** — networks may look different (nodes labeled/ordered differently) while being structurally identical.
- It must learn **all non-trivial structural properties** (degree correlations, community structure, hierarchy, …) without being explicitly trained to capture any of them.

Most state-of-the-art generative graph models rely on deep neural networks — variational auto-encoders, deep Q-networks (reinforcement learning), generative adversarial networks (GANs), and generative recursive neural networks (RNNs). We recommend the 2020 survey ["A systematic survey on deep generative models for graph generation"](https://arxiv.org/abs/2007.06686) by X. Guo and L. Zhao — see [[deep-generative-models-graph-generation-survey.pdf|local copy]].

One application that has attracted large interest is **computational chemistry (molecule design)** and drug synthesis. Discovering a new molecule similar to existing ones (e.g., a set of antibiotics) is expensive and slow, especially if each candidate must be synthesized and tested. Network science and deep learning have been used to propose candidate molecules (graphs of chemical elements) scoring high in similarity to existing molecules. The added challenges: candidate networks must represent **valid molecules** (satisfying each atom's valency for chemical stability), and they should be not just similar but **better** than the given molecules in some property (e.g., a new antibiotic effective against resistant bacteria). A recent survey is ["Deep learning for molecular design"](https://arxiv.org/abs/2007.06686) by D. Elton et al. — see [[deep-learning-molecular-design-review.pdf|local copy]].

## 09 — Advanced Topics: Interdependent Networks

This section introduces **interdependent (or multilayer) networks**, where two or more networks depend on each other so that failures in one can cascade into the others (the canonical example being coupled power-grid and communication networks). The recommended reference is Boccaletti et al., *The structure and dynamics of multilayer networks* — see [[structure-and-dynamics-of-multilayer-networks.pdf|local copy]].

### Video: Interdependent Networks

[[sections/09-advanced-topics-interdependent-networks.mp4]]

Video URL: https://mediaspace.gatech.edu/media/t/1_xwiq9waa

| Text |
|------|
| Another emerging topic in network science is that of Interdependent Networks or  |
| multi-layered networks. This illustration refers to a cascade of power failures that took  |
| place in 2003 in the power distribution network of Italy. We see two networks. On the map  |
| of Italy, we see the network of power generators, while the network of computer servers  |
| that control those power generators is shown at the right over the map of Italy. It is  |
| important to understand that in order for a power generator to operate properly, it has  |
| to be controlled by one of those computer servers. In order for the computer servers to  |
| operate properly, they need to have power. So the two networks are interdependent. At the  |
| first step of the process, one of the power generators shown here in red, went offline.  |
| Three of the computer servers went also offline because they depended on that power  |
| generator. The nodes that are shown in green here are nodes that will go offline at the  |
| next step of the process. Indeed at the next step of the process, some additional  |
| computer servers went offline, causing two more power generators to go offline, shown  |
| here in red. In the final step of the process, as you see, about half of the country went  |
| offline because all of those south power generators went offline together with the  |
| computer servers that control them. This is an example of an interdependent network. In  |
| many real-world systems there are such interdependencies between networks. For example,  |
| in transportation, if there is a disruption in airlines because of a volcanic eruption or  |
| something else, many more passengers will start travelling by trains, buses, or cars,  |
| potentially causing congestion on the land transportation network. |

## 10 — Advanced Topics: Temporal Networks

An active research area in Network Science is the study of **Temporal Networks**. In such networks, nodes and edges may be present only for specific time periods — e.g., a phone-communication network where each call is an edge with a start and end time. Note that **transitivity does not apply** in temporal networks: if A connects to B and B connects to C, we cannot conclude A connects to C.

![[img/10-temporal-networks-1.png|600]]

> Source: "Temporal network metrics and their application to real world networks" (Figure 4.5) by J. K. Tang.

Figure-a represents communications between six people over six time steps — e.g., during the first period $t_1$, node A contacted node B and node C contacted node F. If we ignore the temporal ordering of links, we can reach wrong conclusions about possible communication flows: if A is the only node with some information at $t_1$, can that information ever reach F during the following six time steps? Figure-b shows there are two different **"temporal paths"** from A to F (F obtains the information at $t_4$ on one, at $t_6$ on the other). We could also ask: what is the earliest time each node could receive the information? That is Figure-c, the **"minimum temporal spanning tree"** originating at A.

The temporal structure of edge activations can significantly affect dynamic processes on a network (epidemics, information diffusion, synchronization). Centrality metrics must also be modified for temporal networks so that they only consider temporally-valid paths.

If you are interested to learn more, we recommend the book "A Guide to Temporal Networks" by R. Lambiotte and N. Masuda.

## 11 — Lesson Summary

This lesson focused on the overlap between Network Science and Machine Learning, with an emphasis on Deep Learning and Graph Neural Networks. This is a relatively new area, mostly pursued in the research literature in the last five years or so. The applications are numerous — many real-world problems can be modeled with graphs, and Deep Learning can learn complex features from data without manual "feature engineering".

The main drawbacks of the Deep Learning approach:

- The models are **over-parameterized** (thousands or millions of parameters) — compare with Preferential Attachment (one parameter) or Stochastic Block Graphs (parameters scaling with the number of communities). Too many parameters may overfit the data and be computationally expensive to train.
- Deep Learning models are often **"black boxes"** — not transparent about how the automatically-identified features relate to the task. If a network classifies a node as "bot", we may not know why.
- They typically require **lots of training data**. This is fine for large graphs or many graphs with labeled nodes/edges; for smaller networks, simpler models (Lesson-12) may be more appropriate.

The last part of this lesson also mentioned other state-of-the-art topics (interdependent networks, temporal networks) that we do not have time to cover in more detail; please refer to the provided references.

## 12 — A Final Note

### Video: A Final Note

[[sections/12-a-final-note.mp4]]

Video URL: https://mediaspace.gatech.edu/media/t/1_kuhh5ij6

| Text |
|------|
| We have reached the end of this course. I would like to thank you all for your active  |
| participation during the semester. I hope that you have not only learned some important  |
| things about network analysis, but more importantly, that you are now motivated to keep  |
| exploring and applying this knowledge. And if you end up using network analysis in some  |
| interesting new applications at your work or research, I would love to hear from you in  |
| the future about the challenges that you faced and the practical value of your results.  |
| Please think that and never stop learning. [MUSIC] |
