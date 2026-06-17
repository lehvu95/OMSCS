# Lesson Thirteen — Statistical Analysis of Network Data

> Source: Canvas — CS-7280-O01, OAN (Summer 2026)

## 00 — Lesson Overview

Throughout the lecture, we are giving you some *"food for thought"* — these are questions we suggest you think about as you go through this lesson. You do not need to submit solutions.

### Learning Objectives

Students will:

- Understand some major questions and methods in "network inference"
- Learn key network sampling strategies
- Review link prediction statistical methods
- Infer association networks based on correlation metrics
- Understand the principles of network tomography through theory and case studies

### Required and Recommended Reading

**Required Reading**

- *Sampling and estimation in network graphs*, by Eric D. Kolaczyk, 2009 (Chapter 5 of *Statistical Analysis of Network Data: Methods and Models*) — see [[kolaczyk-mm-ch05.pdf|local copy]].
- *Network inference with confidence from multivariate time series*, by Mark Kramer et al., 2009 — see [[network-inference-confidence-multivariate-time-series.pdf|local copy]].
- *Network topology inference*, by Eric D. Kolaczyk, 2009 (Chapter 7 of *Statistical Analysis of Network Data: Methods and Models*) — see [[kolaczyk-mm-ch07.pdf|local copy]].

**Recommended Reading**

- *What is the real size of a sampled network? The case of the Internet* by Fabien Viger et al., 2007 — see [[real-size-of-sampled-network-internet.pdf|local copy]].

> Applied companion reference: Kolaczyk & Csárdi, *Statistical Analysis of Network Data with R* — shelved in the course textbook library, split by chapter (see [[kolaczyk-r-all.pdf|full book]]; Ch 7 "Network Topology Inference" is the L13-relevant chapter, [[kolaczyk-r-ch07.pdf|local copy]]).

### Assignments

- L13: Knowledge Check
- L13: Quiz

### Video: Introduction to Statistical Analysis of Network Data

[[sections/00-lesson-overview.mp4]]

Video URL: https://mediaspace.gatech.edu/media/t/1_xlezoow0

| Text |
|------|
| The focus of this lesson is the overlap between network science and statistics. A central  |
| question in statistics is, how to estimate certain properties of a population from a  |
| limited sample. In the context of networks, the population may refer to a large family of  |
| networks. Or it may be that the population is a single large network, but we can only  |
| observe a small portion of that network. We start this lesson with a number of sampling  |
| strategies for networks. Additionally we cover network inference problems, in which the  |
| goal is to estimate various properties of the entire network given only a sample of nodes  |
| and ages. Another important problem is how to infer association networks. In such  |
| networks, the edges refer to temporal correlations between the activity of the  |
| corresponding nodes. This problem is important in many disciplines, including  |
| neuroscience and climate science. We will also introduce the network tomography problem,  |
| mostly focusing on topology inference. The goal here is to discover the topology of a  |
| network, given only some parts observations between pairs of nodes. The network  |
| topography approach has been also applied to estimate the characteristics of specific  |
| links, or the flows between network nodes. |

## 01 — Introduction to Network Sampling

It is often the case that we do not know the complete network. Instead, we only have sampled network data, and we need to rely on that sample to infer properties of the entire network. The area of statistical sampling theory provides some general approaches and results that are useful in this goal.

Let us denote the complete network as $G=(V,E)$ — we will be referring to it as the **population graph**. Additionally, we have a sampled graph $G^*=(V^*,E^*)$, which consists of a subset of nodes $V^*$ and edges $E^*$ from the population graph.

To illustrate the challenges involved in network sampling, consider the following problem. Suppose we want to estimate the average degree of the population graph, defined as

$$E[k]= \frac{\sum_{i \in V}k_i}{N}, \quad N=|V|$$

where $k_i$ is the degree of node $i$ and $N$ is the number of nodes in the population graph. The obvious approach is to estimate this with the average degree of the sampled graph $G^*$:

$$\bar{k}= \frac{\sum_{i \in V^*}k_i}{n},\quad n=|V^*|$$

where $n$ is the size of the sample.

Now, consider two different network sampling strategies, or "**designs**". In both of them we start with a random sample $V^*$ of $n$ nodes:

- **Design-1:** for each $i \in V^*$, copy all edges that are adjacent to node $i$ in the set of sampled edges $E^*$.
- **Design-2:** for each pair of sampled nodes $(i,j) \in V^* \times V^*$, examine if they are connected with an edge, i.e., if $(i,j) \in E$. If they are, copy that edge in $E^*$.

Note that Design-1 requires that we know all neighbors of each sampled node, even if those neighbors are not sampled — while Design-2 only observes the adjacencies between sampled nodes. In practice, this means that Design-2 would be simpler or less costly to conduct. Imagine, for example, that we construct a social network based on who is calling whom. Design-1 would require that we know all phone calls of the sampled individuals. Design-2 would require that we only know whether two sampled individuals have called each other.

Which of the two Designs will result in a better estimate of $E[k]$? With **Design-2, we underestimate** the degree of each node by a factor of roughly $\frac{n}{N}$ because, on the average, we only "see" that fraction of nodes of the population graph. That does not mean Design-2 is useless: we could use it and get a reasonable estimate of the average degree as long as we add an appropriate "correction factor", for example:

$$\bar{k}= \frac{N}{n} \frac{\sum_{i \in V^*}k_i}{n}$$

This can be useful if Design-2 is simpler or cheaper to apply than Design-1.

Here is another example: imagine that you want to estimate the number $N$ of nodes in the population network $G$, but you can only collect samples of nodes. How would you estimate $N$? We could use a statistical technique called **capture-recapture estimation**. We first select a random sample $S_1$ of $n_1$ nodes, without replacement, and "mark" these nodes. Then we collect a second sample $S_2$ of $n_2$ nodes, again without replacement. Let $n_3 = |S_1 \cap S_2|$ be the number of nodes that appear in both samples. If $n_3 > 0$, we can estimate the size of the population graph as:

$$\hat{N}=\frac{n_1 \, n_2}{n_{3}}$$

The rationale: the probability that a node is sampled in both $S_1$ and $S_2$ can be estimated as $\frac{n_{3}}{N} = \frac{n_1}{N} \, \frac{n_2}{N}$ because the two samples are independently collected; solving for $N$ gives the estimator.

In sampling theory, two important questions are: (a) Is the estimator **unbiased**, meaning $E[\hat{N}]=N$? (b) What is the **variance** of the estimator? For instance, the variance of $\hat{N}$ is:

$$V({\hat{N}}) = \frac{n_1 \, n_2\, (n_1-n_{3}) \, (n_2-n_{3})}{{n_{3}}^3}$$

Suppose $n_1=n_2=1000$ and $n_3=1$. Our estimate is $\hat{N}=10^6$ — but that is also the standard deviation of $\hat{N}$, making the estimate useless! If $n_3=100$, however, we get $\hat{N}=10{,}000$ with a standard deviation of about 900, which is much more reasonable.

**Food For Thought**

For the estimator $\hat{N}$, show that if $n_1$ and $n_2$ are fixed, the variable $n_3$ follows the hypergeometric distribution. Use this to derive the previous expression for the variance of $\hat{N}$.

## 02 — Network Sampling Strategies

### Video: Network Sampling Strategies

[[sections/02-network-sampling-strategies.mp4]]

Video URL: https://mediaspace.gatech.edu/media/t/1_tq6nql60

| Text |
|------|
| There are various ways to sample from a network and they result in subgraphs with very  |
| different properties. Here we introduce four of the most common network sampling  |
| strategies. Suppose that the network has n nodes and we want to sample k of them. The  |
| simplest sampling strategy is to choose randomly and without replacement k out of n  |
| nodes. And Ned's of the original network is included in the sample only if both its end  |
| points are sampled. In this example, the yellow nodes are the K sampled nodes, but the  |
| only sampled edges are those highlighted in orange. This is referred to as induced  |
| subgraph sampling. Suppose now that the network has m edges and we want to sample k of  |
| them. Another simple sampling strategy is to select randomly and without replacement k  |
| edges. And now it is included in the sample as long as it is adjacent or incident to a  |
| sampled edge. This is why this method is referred to as incident subgraph sampling. In  |
| this visualization, the yellow edges have been sampled while the orange nodes are  |
| included in the sample because they are adjusting to at least one sampled edge. Note that  |
| higher degree nodes are more likely to be sampled this way. In other words, this is a  |
| biased sampling strategy in terms of node sampling probabilities. Another sampling  |
| strategy referred to as snowball sampling is to start from a set of randomly selected  |
| nodes referred to as seeds sown in yellow here. In the first wave of the process, we  |
| include in the sample all the nodes and edges that are adjacent to the seeds. These are  |
| shown in orange. In the second wave, we include all the nodes and edges that are adjacent  |
| to the notes of the first wave and that have not been sampled already. Bees are shown in  |
| red. This process continues until we have included in the sample a desirable number of  |
| nodes or edges. Or we have reached the point in which we cannot sample anymore. The  |
| special case of a single sampling wave is referred to as star sampling. Another family of  |
| sampling strategies is referred to as link tracing. It is similar with snowball sampling  |
| in the sense that we start from some seed nodes. But here we denote sample all the edges  |
| and nodes. Instead, there is a criterion that specifies which adjusts and note to sample  |
| at each step. For instance, in computer networks, we can perform a trace route sampling.  |
| Here the seeds that are sown in yellow as S1 and S2 are referred to as the source nodes  |
| of the trace routes. And we are also given a set of target nodes. So here is T1 and T2.  |
| The network uses a specific route to connect a source to a target. And that is exactly  |
| the sequence of nodes and edges we include in the sample. So in here in orange, the  |
| sample in this case depends both on the chosen sources and targets, but also on the  |
| routing strategy that is deployed in that network. |

## 03 — Inclusion Probabilities with Each Sampling Strategy

An important question for each sampling strategy is: what is the probability that a given sampling strategy includes a node or an edge in the sample? As we will see, these probabilities are essential in deriving important network estimators.

> Image source: Kolaczyk, Eric D. *Statistical Analysis of Network Data: Methods and Models* (2009), Springer.

For **induced subgraph sampling**, the node and edge inclusion probabilities are, respectively:

$$\pi_i = \frac{n}{N}, \quad \pi_{(i,j)}=\frac{n(n-1)}{N(N-1)}$$

where $n$ is the number of sampled nodes — because each node of the population graph is sampled uniformly at random without replacement, and each edge is sampled if both its endpoints are sampled. Note the node (and edge) inclusion probability is the same for all nodes.

![[img/03-induced-subgraph-sampling.png|400]]

For **incident subgraph sampling**, we sample $n$ edges randomly and without replacement. The inclusion probability for edges is simply $\pi_{(i,j)}=n/|E|$, where $|E|$ is the number of edges in the population graph. The inclusion probability for node $i$ is one minus the probability that none of the $k_i$ edges of node $i$ is sampled:

$$\pi_i = 1 - \frac{\binom{|E|-k_i}{n}}{\binom{|E|}{n}},\quad \mbox{if }n\leq |E|-k_i$$

Of course if $n > |E|-k_i$, then $\pi_i=1$. Note that, with incident subgraph sampling, nodes of higher degree have a higher inclusion probability.

![[img/03-incident-subgraph-sampling.png|400]]

With **snowball sampling** (the yellow nodes are the seeds and the process has two stages: first orange nodes and then brown nodes), the inclusion probabilities are harder to derive, especially when the snowball process includes multiple stages. The statistical literature provides some approximate expressions.

![[img/03-snowball-sampling.png|400]]

With **link tracing** (including traceroute sampling), the inclusion probabilities are also harder to derive. Suppose the "traceroutes" (sampled paths from source nodes to target nodes) follow only shortest-paths, a fraction $\rho_s$ of nodes is marked as sources while another fraction $\rho_t$ of nodes is marked as targets, and $b_i$ is the betweenness centrality of node $i$ while $b_{(i,j)}$ is the betweenness centrality of edge $(i,j)$. Then, the node and edge inclusion probabilities are approximately:

$$\pi_i \approx 1-(1-\rho_s-\rho_t)e^{-\rho_s\rho_t b_i}, \quad \pi_{(i,j)}\approx 1 - e^{-\rho_s\rho_t b_{(i,j)}}$$

![[img/03-link-tracing-sampling.png|400]]

**Food For Thought**

Search the literature to find at least an approximate expression for the inclusion probability of nodes and edges in two-step snowball sampling.

## 04 — Horvitz-Thompson Estimation of "Node Totals"

Let us now use the previous inclusion probabilities to estimate various "node totals", i.e., metrics defined based on the summation of a metric across all nodes. Specifically, suppose each node $i$ has some property $y_i$. We often want to estimate the total value of that property across the whole network:

$$\tau=\sum_{i\in V}y_i$$

For instance, if $y_i$ is the degree of each node, then $\tau$ gives the average node degree (divide by $N$); if $y_i$ indicates whether a node is a bot, then $\tau$ is the total number of bots; if $y_i$ is a node capacity, $\tau$ is the total capacity.

Suppose we have a sample $S$ of $n$ nodes and we know the value $y_i$ of each sampled node. An important result is the **Horvitz-Thompson estimator**:

$$\hat{\tau} = \sum_{i \in S}\frac{y_i}{\pi_i}$$

where $\pi_i$ is the inclusion probability of node $i$, as long as $\pi_i > 0$ for all nodes in $S$. In other words, to estimate the "total value" we should not just add the sampled values and multiply by $N/n$ (that would be okay only if $\pi_i=\frac{n}{N}$ for all $i$). Instead, we normalize the value of each sampled node by its sampling probability.

A key property is that the estimator is **unbiased**. Let $Z_i$ be an indicator that equals one if node $i$ is sampled in $S$ and 0 otherwise. Then:

$$E[\hat{\tau}] = E\left[\sum_{i \in S}\frac{y_i}{\pi_i}\right]= E\left[\sum_{i \in V}\frac{y_i\, Z_i}{\pi_i}\right]=\sum_{i \in V}\frac{y_i\, E[Z_i]}{\pi_i}= \sum_{i \in V} y_i = \tau$$

An estimate of the variance can be calculated from the sample $S$:

$$V(\hat{\tau}) \approx \sum_{i\in S}\sum_{j\in S}y_i y_j\left(\frac{\pi_{i,j}}{\pi_i \pi_j}-1\right)$$

where $\pi_{i,j}$ is the probability that both nodes $i$ and $j$ are sampled in $S$ (when $i=j$, we define $\pi_{i,j}=\pi_i$).

**Food For Thought**

Suppose that $i$ and $j$ are sampled independently. How would you simplify the previous expression for the variance of the Horvitz-Thompson estimator?

## 05 — Estimating the Number of Edges and the Average Degree

We can also apply the Horvitz-Thompson estimator to "totals" defined over all possible node pairs. Here, each node pair $(i,j)\in V\times V$ is associated with a value $y_{i,j}$, and we want to estimate the total $\tau = \sum_{(i,j)\in V \times V}y_{i,j}$. For instance, if $y_{i,j}$ is one when the two nodes are connected and zero otherwise, the total $\tau$ is twice the number of edges in the population graph. Another example: if $y_{i,j}$ is one if the shortest path between the two nodes traverses a given node $k$, then $\tau$ is related to the betweenness centrality of node $k$.

Given a sample $S$ of $n$ nodes with the corresponding values $y_{i,j}$, the Horvitz-Thompson estimator gives the unbiased estimator $\hat{\tau}=\sum_{(i,j)\in S\times S} \frac{y_{i,j}}{\pi_{i,j}}$.

Let us apply this to estimating the **number of edges**. With induced subgraph sampling (starting with $n$ nodes chosen without replacement), the probability of sampling a node pair $(i,j)$ is

$$\pi_{i,j} = \frac{\binom{n}{2}}{\binom{N}{2}} = \frac{n(n-1)}{N(N-1)}$$

So our estimate for the number of edges is:

$$\hat{\tau}=\frac{1}{2}\sum_{(i,j)\in S\times S}\frac{y_{i,j}}{\pi_{i,j}}=|E^*|\frac{N(N-1)}{n(n-1)}$$

which means we just multiply the number of sampled edges $|E^*|$ by a correction factor (the inverse of the fraction of sampled node pairs).

![[img/05-yeast-ppi-edge-estimation.png|600]]

> Image source: Kolaczyk, Eric D. *Statistical Analysis of Network Data: Methods and Models* (2009), Springer.

To put these results in an empirical setting, the plot shows the results of estimating the network density (and thus the number of edges) in the Yeast protein-protein interaction network, using induced subgraph sampling. The actual number of edges is 31,201 (number of nodes is 5,151). The plots at the left show the empirical distribution of the sampled number of edges $|E^*|$ for three node sampling fractions ($p=0.10, 0.20, 0.30$); the plots at the right show the empirical distribution of the standard error. All distributions are based on 10,000 trials.

Now use this result to estimate the **average degree** $E[k]$. Recall $E[k]= \frac{2|E|}{N}$. Using the previous estimate for the number of edges:

$$\bar{k}_{\mbox{induced-subgraph}} = \frac{2}{N}\, |E^*|\frac{N(N-1)}{n(n-1)}= \frac{2\, |E^*|}{n} \, \frac{N-1}{n-1}$$

Compare this with the average-degree estimate under single-stage snowball sampling (also known as **star sampling**), where we sample all the neighboring edges of each sampled node, so we know the exact degree $k_i$ of each sampled node and the inclusion probability for each node is $n/N$. The Horvitz-Thompson estimator for the total number of edges is $\frac{1}{2}\sum_{i \in S}\frac{k_i}{n/N}$, so the star-sampling estimate for the average degree is:

$$\bar{k}_{\mbox{star-sampling}} = \frac{2}{N} \left( \frac{1}{2}\sum_{i \in S}\frac{k_i}{n/N} \right)=\frac{2 \, |E^*|}{n}$$

The induced-subgraph estimator differs from the star-sampling estimator by a factor $\frac{N-1}{n-1}$, which corrects for the extent to which the degree of each node is under-sampled when we use induced subgraph sampling.

**Food For Thought**

Recall that the Transitivity of a graph requires us to calculate the number of connected node triplets and triangles. How would you apply the previous framework to estimate these quantities from a sample, using induced subgraph sampling?

## 06 — Estimating the Number of Nodes with Traceroute-like Methods

Let us now see how we can use a traceroute-like sampling strategy to estimate the number of nodes in a large network. Suppose that we have a set of sources $S=\{s_1,s_2,\dots,s_{n_S}\}$ and a set of targets $T=\{t_1,t_2,\dots,t_{n_T}\}$. Each traceroute starts from a source node and traverses a network path to a target node, also "observing" (sampling) the intermediate nodes along the path. Note that an intermediate node may be observed in more than one traceroute path. The number of observed nodes is denoted by $N^*$, while the number of nodes in the population network is denoted by $N$. How can we use $N^*$ to estimate $N$?

The key idea is as follows: suppose that we drop a given target node $t_j$ from the study. Would that target be observed in the traceroute paths to the remaining targets? We can easily measure the fraction of targets that would be observed in this manner. Intuitively, the lower this fraction is, the larger the population network we are trying to sample. Can we use this fraction to "inflate" $N^*$ so that it gives us a good estimate of $N$? As we will see, the answer is yes, through a simple mathematical argument.

Let us introduce some notation. Suppose that $V^*_{(-j)}$ is the set of observed nodes when we drop $t_j$ from the set of targets. The number of such nodes is $N^*_{(-j)}=|V^*_{(-j)}|$.

The binary variable $\delta_j$ is equal to one if $t_j$ is NOT observed on sampled paths to any other target — and zero otherwise. The total number of such targets (that can be observed only if we traceroute directly to them) is $X=\sum_j \delta_j$.

The probability that $t_j$ is not observed on the paths to any other target is simply the ratio between the number of nodes that are not observed after we remove $t_j$, and the number of non-source and non-target nodes:

$$P\left(\delta_j=1 \mid V^*_{(-j)}\right) = \frac{N-N^*_{(-j)}}{N-n_S-(n_T-1)}$$

assuming that the targets are chosen through random sampling without replacement from the set of all non-source nodes in the population graph.

The expected value of $N^*_{(-j)}$ is the same for all $j$, simply due to symmetry ($j$ can be any of the targets). Let us denote that expected value as $E\left[N^*_{(-)}\right]$. So the expected value of $X$ is:

$$E[X]=\sum_{j=1}^{n_T} P\left(\delta_j=1 \mid V^*_{(-j)}\right) = n_T \, \frac{N-E\left[N^*_{(-)}\right]}{N-n_S-(n_T-1)}$$

We have now reached our goal: we can solve the last equation for the size of the population graph $N$:

$$N = \frac{n_T \, E\left[N^*_{(-)}\right] - (n_S+n_T-1)\,E[X]}{n_T - E[X]}$$

The expected value $E[X]$ of the targets that can be observed only if we traceroute to them can be estimated by $X$, which is directly available from our traceroute data. And the expected value $E\left[N^*_{(-)}\right]$ can be estimated, again directly from our traceroute data, as the average of $N^*_{(-j)}$ across all targets $j$.

![[img/06-traceroute-size-estimation.png|600]]

> Image source: Kolaczyk, Eric D. *Statistical Analysis of Network Data: Methods and Models* (2009), Springer.

Let us now see what happens when this method is applied to estimate the size of an older snapshot of the Internet that included $N=624{,}324$ nodes and $1{,}191{,}525$ edges. The number of sources was $n_S=10$. The "target density", defined as $\rho_T=n_T/N$, is shown as the x-axis variable in the graph above. The y-axis shows the fraction of the estimated network size over the actual network size (ideally it should equal 1). The solid dots show the estimates from the method described above (including intervals of $\pm$ one standard deviation around the mean). The open dots show the same fraction if we had simply estimated the size of the network based on $N^*$.

Note that this method is fairly accurate even if the target density is as low as 0.005 (i.e., about 3,100 targets). On the contrary, if we had estimated the size of the network simply based on the number of observed nodes $N^*$, we would grossly underestimate how large the network is (unless our targets pretty much cover all network nodes).

**Food For Thought**

If you could place the $n_S$ sources anywhere you want, where would you place them to improve this estimation process?

## 07 — Topology Inference Problems

Let us now move from network sampling to a different problem: **topology inference**. How can we estimate the topology of a network from incomplete information about its nodes and edges?

> Image source: Kolaczyk, Eric D. *Statistical Analysis of Network Data: Methods and Models* (2009), Springer.

![[img/07-topology-inference-variations.png|500]]

The problem of topology inference has several variations, illustrated above. The top-left figure shows the actual (complete) network: five nodes and five edges (solid dark blue), with dotted dark blue lines for node pairs NOT connected. The variations are:

a) **Link prediction:** (top-right) we know that certain node pairs are connected (solid dark blue) or NOT connected (dotted dark blue) — but we do not know about the remaining node pairs (solid/dotted light blue). We saw link prediction in Lesson-12 via the Hierarchical Random Graph (HRG) model; here we will solve it without HRG.

b) **Association networks:** (bottom-left) we know the set of nodes but have no information about the edges. Instead, we have data about node characteristics (temporal activity, attributes), and we use node similarity to infer which pairs are connected.

c) **Network tomography:** (bottom-right) we know some nodes (red) but not others (pink) — and may not know the edges either. This is the hardest topology inference problem, but progress is possible with "on-demand path measurements" from the known nodes, especially when the underlying network is a tree.

## 08 — Link Prediction

Let us introduce the Link Prediction problem with an example. The following network refers to a set of 36 lawyers (partners and associates) working for a law firm in New England. Two lawyers are connected if they indicated (through a survey) that they have worked together on a case. We know several attributes for each lawyer: seniority (the number next to each node), gender (nodes 27, 29, 34 are females), office location (the shape of the node — three locations), and type of practice (red for Litigation, cyan for Corporate Law).

![[img/08-lawyers-collaboration-network.png|500]]

> Source: "Statistical analysis of network data" by E. D. Kolaczyk.

Suppose we observe a portion of this graph but not the whole thing. How would you infer whether two apparently-disconnected nodes are actually connected? We can rely on two sources: (a) **node attributes** — e.g., two lawyers may be more likely to work together if they share office location and both practice corporate law; (b) **topological information** from the known edges — e.g., if $A$ and $B$ share no common neighbors, it may be unlikely they are connected.

We assume the missing edges are **randomly missing** — whether an edge is observed does not depend on its own attributes. Let us define topological "features". For a node $i$, let $N_i^{obs}$ be its set of observed neighbors. If two nodes have highly overlapping observed neighbors, they are probably connected. A common metric is the **Jaccard similarity**:

$$s(i,j)=\frac{|N_i^{obs}\cap N_j^{obs}|}{|N_i^{obs}\cup N_j^{obs}|}$$

which equals one if $i$ and $j$ have identical observed neighbors. Another metric, the **Adamic-Adar similarity**, is:

$$s(i,j) = \sum_{k \in N_i^{obs} \cap N_j^{obs}} \frac{1}{\log|N_k^{obs}|}$$

Here $k$ is a common neighbor of both $i$ and $j$; if $k$ is highly connected it does not add much evidence, but if $k$ is connected only to $i$ and $j$ it makes that connection more likely.

Together with topological scores $s(i,j)$, we can use node attributes to construct predictor variables for every node pair. For the lawyer example:

$$Z_{i,j}^{(1)} = \mbox{seniority}_i + \mbox{seniority}_j$$
$$Z_{i,j}^{(2)} = \mbox{practice}_i + \mbox{practice}_j$$
$$Z_{i,j}^{(3)} = 1 \mbox{ if practice}_i = \mbox{practice}_j, \mbox{ else } 0$$
$$Z_{i,j}^{(4)} = 1 \mbox{ if gender}_i = \mbox{gender}_j, \mbox{ else } 0$$
$$Z_{i,j}^{(5)} = 1 \mbox{ if office}_i = \mbox{office}_j, \mbox{ else } 0$$

and a topological score, e.g. $Z_{i,j}^{(6)} = |N_i^{obs} \cap N_j^{obs}|$.

Now we design a binary classifier using **Logistic Regression**. Let $\mathbf{Y}$ be the complete adjacency matrix; the training data is the set of observed node pairs $\mathbf{Y}^{obs}$, and the unknown pairs are $\mathbf{Y}^{miss}$. The logistic regression model is:

$$\log\left[ \frac{P(Y_{i,j}=1\mid \mathbf{Z}_{i,j}=\mathbf{z})}{P(Y_{i,j}=0\mid \mathbf{Z}_{i,j}=\mathbf{z})} \right] = \mathbf{\beta^T \, z}$$

where $\mathbf{z}$ includes all predictor variables for the node pair and $\mathbf{\beta}$ is the (shared) vector of regression coefficients. After training on the observed pairs, we predict whether a missing pair is connected:

$$P(Y_{i,j}^{miss}=1\mid \mathbf{Z}_{i,j}=\mathbf{z})= \frac{e^{\mathbf{\beta^T z}}}{1+e^{\mathbf{\beta^T z}}}$$

If this probability exceeds 0.5 for a pair $(i,j)$, we infer the two nodes are connected. The framework is general — any binary classifier (SVM, neural network) could replace logistic regression.

**Food For Thought**

In this framework the logistic regression coefficients are the same for every node pair. What does this assume about the structure of the network? How would you compare this approach with link prediction using HRG (Lesson-12)?

## 09 — Association Networks

In some cases we know the nodes of the network but none of the edges. Instead, we have observations of the state of each node, and we know that the state of a node depends on the state of the nodes it is connected with. For instance, in climate science the nodes may be geographical regions with time series of temperature, precipitation, pressure; spatial correlations between regions (e.g., the sea-surface-temperature link between the Indian Ocean and a Pacific region) define an "association network". We saw a related problem in Lesson-8 with the $\delta$-MAPS method, but our focus then was on identifying the regions, not the association network between them.

Formally, suppose we have $N$ nodes, and for each node $i$ a random vector $X_i$ of $m$ independent observations. We want an undirected network in which two nodes $i$ and $j$ are connected if $X_i$ and $X_j$ are sufficiently "associated". Three questions must be answered: (a) which **association metric** to use; (b) how to determine **statistical significance**; (c) how to control the rate of **false positives**.

**Association metric.** The simplest is **Pearson's correlation coefficient**:

$$\rho_{i,j} = \frac{E[(X_i-\mu_i)(X_j-\mu_j)]}{\sigma_i \, \sigma_j}$$

where $\mu_i$ and $\sigma_i$ are the mean and standard deviation of $X_i$. It detects linear dependencies; if $X_i$ and $X_j$ are independent then $\rho_{i,j}=0$ (the converse may not hold). Alternatives include Spearman's rank correlation (robust to outliers), mutual information (detects non-linear correlations), and partial correlations (to remove the effect of a third variable $X_k$).

**Statistical significance.** The null hypothesis is $H_0: \rho_{i,j}=0$ versus $H_1: \rho_{i,j}\neq 0$. To test it we need the distribution of $\rho_{i,j}$ under $H_0$. Apply the **Fisher transformation**:

$$z_{i,j}=\frac{1}{2}\log\left[ \frac{1+\rho_{i,j}}{1-\rho_{i,j}}\right]$$

so that instead of being limited to $[-1,+1]$, the metric varies over $(-\infty, \infty)$. A statistical result: if $(X_i,X_j)$ are uncorrelated and bivariate Gaussian, then $z_{i,j}$ follows a Gaussian with zero mean and variance $1/(m-3)$, where $m$ is the dimension of $X_i$. This gives a $p$-value for each correlation.

![[img/09-gene-correlation-scatter.png|450]]

> Image source: Kolaczyk, Eric D. *Statistical Analysis of Network Data: Methods and Models* (2009), Springer.

For example, the scatter plot shows $m=445$ observations of the expression levels of two *E. coli* genes, `tyrR` and `aroG`, with $\rho=0.43$. Applying the Fisher transformation gives $z=0.4599$; the probability that a zero-mean Gaussian with variance $1/(445-3)\approx0.0023$ produces a value of $0.4599$ is less than $7.69\times10^{-22}$, which is the $p$-value. So the two genes are significantly correlated and should be connected.

**Controlling false positives.** Suppose we have $N=1000$ nodes and thus $m=N(N-1)/2 = 499{,}500$ potential edges, and we call a correlation significant if its $p$-value is below 1%. Even if NONE of the correlations are real, applying the test 499,500 times would incorrectly reject $H_0$ in 1% of cases — about **4,995 spurious edges**. This is the **Multiple Testing problem**. A common remedy is the **False Discovery Rate (FDR)** method of Benjamini and Hochberg, controlling the false-positive rate $\alpha$. Sort the $p$-values from lowest to highest, $p_{(1)}\leq p_{(2)} \leq \dots p_{(m)}$, and find the highest $k$ such that

$$p_{(k)}\leq \frac{k}{m}\alpha$$

(otherwise $k=0$). The null hypothesis is rejected for the $k$ lowest $p$-values, so we "discover" only those $k$ edges. Benjamini and Hochberg proved that if the $m$ tests are independent, the false-positive rate is below $\alpha$.

![[img/09-benjamini-hochberg-procedure.png|450]]

> Image source: "The power of the Benjamini-Hochberg procedure", by W. van Loon.

In association-network inference, the test-independence assumption typically does not hold; more sophisticated FDR-control methods exist for that case.

**Food For Thought**

a) Explain why the $m$ tests are probably not independent in association network inference.

b) What would you do if the Benjamini-Hochberg method gives $k=0$ for the $\alpha$ you want, and you are not allowed to increase $\alpha$?

## 10 — Topology Inference Using Network Tomography

Let us now focus on topology inference using **network tomography**. In medical imaging, "tomography" observes the internal structure of a system using only measurements from its exterior or "periphery". For networks, the internal structure is the topology (both nodes and edges), while the "periphery" is a few observable nodes we can use for measurements.

![[img/10-tomography-tree-network.png|450]]

> Image source: Kolaczyk, Eric D. *Statistical Analysis of Network Data: Methods and Models* (2009), Springer.

For instance, in the tree network above, the observable nodes are the root (blue) and the leaves (yellow); all internal nodes (green) and the edges are unknown. We describe network tomography in the context of **computer networks** (nodes are routers, edges are transmission links), though the methods are general (e.g., inference of phylogenetic trees).

A basic fact: when a packet of size $L$ bits is transmitted on a link of capacity $C$ bits-per-second, the transmission takes $L/C$ seconds; a second packet must wait $L/C$ at the router buffer. We exploit this with **"sandwich probing"**. The root sends three packets P1, P2, P3 at the same time: P1 and P3 are small (minimum size) and destined to one observable node $R_i$, while the intermediate packet P2 is large (maximum size) and destined to another observable node $R_j$. The receiving node $R_i$ measures the end-to-end delay of the two small packets.

If $R_i$ and $R_j$ are reachable through completely different paths, P3 is never delayed by P2 — the delays of P1 and P3 are very similar, and their absolute difference is close to 0. If $R_i$ and $R_j$ share highly overlapping paths, P3 is delayed by P2 at every intermediate router in the overlapping segment — the more shared routers, the larger the extra delay of P3. Let $d_{i,j}$ denote the difference between the transfer delays of P1 and P3 when sent to $R_i$ while the large packet P2 goes to $R_j$; this carries information about the path overlap. In practice we repeat this thousands of times and average $d_{i,j}$.

![[img/10-delay-difference-matrix.png|450]]

> Image source: Kolaczyk, Eric D. *Statistical Analysis of Network Data: Methods and Models* (2009), Springer.

The figure above visualizes the average delay differences for an experiment in which about 10,000 "packet sandwiches" were sent from a computer at Rice University to ten destinations (two also at Rice, others at US universities, and two — IST and IT — in Portugal). Darker color is a lower value (closer to 0); brighter color is higher. When the small packets go to a Rice destination and the large packet outside Rice, the delay difference is low relative to the case where both destinations are outside Rice.

Now that $d_{i,j}$ is a metric of "path similarity", we apply a **hierarchical clustering algorithm** to infer a binary tree rooted at the source, with all destinations at the leaves — identifying the tree that best explains the delay differences. The algorithm proceeds iteratively: at each step it identifies the two leaves $i$ and $j$ with the largest delay difference (highest path overlap), groups them under a new internal node $a(i,j)$, and sets the delay difference between $a(i,j)$ and any other leaf $k$ to the average of $d_{i,k}$ and $d_{j,k}$ (average linking). The grouped leaves are marked "covered"; the algorithm continues until all nodes are covered.

![[img/10-actual-vs-inferred-tree.png|550]]

> Image source: Kolaczyk, Eric D. *Statistical Analysis of Network Data: Methods and Models* (2009), Springer.

The figure shows the result on the delay-difference data: the top visualization is the actual network paths from the Rice source to the ten destinations; the bottom is the inferred tree. The inferred network is a binary tree while the actual one has branching routers with more than two children, and one router (IND) is missing from the inferred network — probably because it is so far that it does not measurably increase the delay of P3.

**Food For Thought**

a) The metric here is based on delay variations using "packet sandwiches". Can you think of other ways to probe a network to measure topological overlap of paths?

b) The inference method here is hierarchical clustering. Can you think of other network inference methods? (Hint: the dendrogram of the HRG model in Lesson-12.)

## 11 — Other Network Estimation and Tomography Problems

### Video: Other Network Tomography Problems

[[sections/11-other-network-estimation-and-tomography-problems.mp4]]

Video URL: https://mediaspace.gatech.edu/media/t/1_ldfgrmjd

| Text |
|------|
| There are several other interesting problems in the network tomography literature. Here  |
| we simply mention a couple of them. In a computer network, links can be in a congested  |
| state, causing performance problems, such as queuing delays or packet losses in every  |
| end-to-end path that goes through those links. Suppose that we have a number of sensors  |
| and we can monitor the performance of several end-to-end paths shown here in red between  |
| those sensors. If none of the links is congested, then all of the paths will appear as  |
| not congested. If however, one link becomes congested, then the paths that go through  |
| that link will also appear in the path measurements as congested. In this visualization,  |
| the two orange paths are congested and they may be introducing large queuing delays and  |
| packet losses. Which link do you think is the cause of these problems? If we assume that  |
| there is only one congested link and congestion can only take place between routers, not  |
| between sensors and routers, then the most parsimonious explanation in this scenario  |
| here, is that the link that is shared by both congested paths, shown here in red, is also  |
| congested. In general, as long as we know the topology of the network and they're out  |
| between every pair of sensor nodes, we can usually identify the link or sequence of links  |
| that may be congested. In the context of communication networks, each link is associated  |
| with the propagation delay. Suppose that we want to estimate these link delays given  |
| end-to-end delay measurements. The delay of a path is equal to the sum of the link delays  |
| in that path. For instance, in this small network we see here we have three links with  |
| unknown delays. Suppose that we measure using a software tool such as Pink, that the  |
| delay in the path between A and B is 30 milliseconds, between A and C is 40 milliseconds,  |
| and between B and C is 50 milliseconds. Further, suppose that we know the topology of the  |
| network and the route or sequence of links in its path. We can express this problem as a  |
| system of linear equations in which the unknowns are the link delays and each equation  |
| corresponds to a distinct path. In this case, the linear system has a unique solution for  |
| the delay of each link shown here in the visualization. In practice however, such systems  |
| are often under constraint because the number of unknowns, the number of links, is more  |
| than the number of equations or paths. In such cases, we need to make additional  |
| assumptions about the links in order to be able to solve the linear system. Another  |
| interesting tomography problem in the context of transportation or communication networks  |
| is to estimate the amount of flow or traffic between every pair of end-points. This is  |
| also known as the traffic matrix inference problem. For instance, in this visualization  |
| we have four antinodes, the cities Atlanta, Boston, Chicago, and Detroit. The directed  |
| flows between these four cities may refer to the number of trucks driving between the  |
| cities every day. Suppose that we know the underlying road network and the route that is  |
| followed between every pair of cities. Further, suppose that we know for each of these  |
| links, the traffic volume on that link, it could be the number of trucks per day on that  |
| highway segment. How would you use such link level traffic volumes to estimate the  |
| unknown path level directed flows? Try to write down a system of linear equations for  |
| this network, so that each of the directed flows between two cities corresponds to an  |
| unknown and its network link gives us an equation. As you will see in many cases, we have  |
| more unknowns than equations, meaning that again we're dealing with an underspecified  |
| problem. As we just saw the traffic matrix inference problem is often under-constrained  |
| because the number of unknowns is typically larger than the number of equations. One way  |
| to add some more structure into the problem is to consider a model that describes the  |
| traffic flow between two-end nodes based on certain properties of those nodes, such as  |
| the population or the distance between them. A common sets model is the traffic gravity  |
| model. This model assumes that the traffic between two cities is proportional to the  |
| product of the populations PI and PJ of the two cities, and inversely proportional to the  |
| distance between the two cities, shown here as DIJ. The proportionality coefficient K is  |
| a variable that we can estimate based on the link level traffic volume measurements.  |
| Additional constraints are typically sufficient to solve the traffic matrix estimation  |
| problems we have in practice. |

## 12 — Lesson Summary

This lesson focused on the use of statistical methods in the analysis of network data. This is a broad area; we mostly focused on two topics:

a) **network sampling:** design of different sampling strategies and inference of network properties from those samples;

b) **topology inference:** detecting the presence of missing links, creating association networks, and using tomography methods to discover the topology of the network.

Here is a list of other topics in the statistical analysis of network data:

- Statistical modeling and prediction of dynamic processes on networks (e.g., Markov Random Fields or Kernel-Based Regression on processes such as epidemics)
- Analysis and design of directed and undirected graphical models
- Efficient algorithms for the computation of network motifs from sampled network data
- Efficient algorithms for the computation of centrality metrics and communities

In parallel, some of these problems are also pursued by the Machine Learning community, as we will see in the next lesson.
