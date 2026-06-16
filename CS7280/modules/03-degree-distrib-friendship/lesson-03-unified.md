# Lesson Three — Degree Distribution and The "Friendship Paradox"

> Source: Canvas — CS-7280-O01, OAN (Summer 2026)

Throughout the lecture, we are giving you some *"food for thought"*, these are questions we suggest you think about as you go through this lesson. You do not need to submit solutions.

## 00 — Lesson Three Overview

### Learning Objectives

Students will be able to:

- Measure and interpret the degree distribution of a network
- Understand the *"friendship paradox"* to illustrate the importance of the degree distribution
- An application of the friendship paradox: vaccination targets when the network topology is unknown
- Learn the $G(n,p)$ model as the most basic type of random graph
- Degree correlations and assortative networks

### Required and Recommended Reading

**Required Reading**

- Chapter-3 from A-L. Barabási, [Network Science](http://www.networksciencebook.com/), 2015.
- Chapter-7 (sections 7.1, 7.2, 7.3, 7.5) from A-L. Barabási, [Network Science](http://www.networksciencebook.com/), 2015.

**Recommended Reading**

- [Simulated Epidemics in an Empirical Spatiotemporal Network of 50,185 Sexual Contacts](http://www.ploscompbiol.org/article/info%3Adoi%2F10.1371%2Fjournal.pcbi.1001109#s2). Luis E. C. Rocha, Fredrik Liljeros, Petter Holme (2011). See [[readings/Simulated Epidemics in an Empirical Spatiotemporal.pdf|local copy]].

### Assignments

- L3: Knowledge Check
- L3: Quiz

### Video: Introduction to Degree Distribution and The "Friendship Paradox"

[[sections/00-lesson-overview.mp4]]

Video URL: https://mediaspace.gatech.edu/media/t/1_7055fv78

| Text |
|------|
| The objective of this lesson is to introduce you to what we mean by degree distribution |
| of a network and to understand its significance. We will also talk about the friendship |
| paradox, which is related to the variance of the degree distribution. And we will see how |
| to apply the friendship paradox in the context of immunization strategies. Then, we will |
| introduce the simplest random graph model called GNP and study degree distribution and |
| mathematical properties. Finally, we will discuss networks in which the degrees of edges |
| and nodes are correlated. |

## 01 — Degree Distribution

![[img/01-degree-distribution.png|600]]

The degree distribution of a given network shows the fraction of nodes with degree $k$.

If we think of networks as random samples from an ensemble of graphs, we can think of $p_k$ as the probability that a node has degree $k$, for $k \geq 0$.

The network in this visualization has six nodes and the plot shows the empirical probability density function *(which is a histogram)* for the probability $p_k$.

## 02 — Degree Distribution Moments

Recall that, given the probability distribution of a random variable, we can compute the first moment *(mean)*, second moment, variance, etc.

The moments that we will mostly use in this course are the average degree, the second moment of the degree *(the average of the squared degrees)*, and the variance of the degree distribution:

$$\overline{k} = \sum_k k\, p_k \qquad \overline{k^2} = \sum_k k^2 p_k \qquad \sigma_k^2 = \overline{k^2} - \overline{k}^2$$

### Complementary Cumulative Distribution Function

![[img/02-ccdf.png|600]]

For larger networks, we usually do not show the empirical probability density function $p_k$. Instead, we show the probability that the degree is at least $k$, for any $k \geq 0$.

This is referred to as the Complementary Cumulative Distribution Function *(denoted as C-CDF)*. Note that $\overline{P_k}$ = Prob[degree $\geq k$] is the sum of all $p_x$ values for $x \geq k$.

## 03 — Two Special Degree Distributions

![[img/03-two-special-distributions.png|600]]

The C-CDF plots are often shown using a logarithmic scale at the x-axis and/or y-axis. Here is why.

Suppose that the C-CDF decays exponentially fast. In a log-linear plot *(as shown at the left in the image above)*, this distribution will appear as a straight line with slope $-\lambda$. The average degree in such networks is $1/\lambda$. The probability that a node has degree at least $k$ drops exponentially fast with $k$.

On the other hand, in many networks, the C-CDF decays with a power-law of $k$. For example, if $\alpha = 2$, the probability to see a node with a degree at least $k$ drops proportionally to $1/k^2$. In a log-log plot *(as shown at the right)*, this distribution will appear as a straight line with slope $\alpha$. As we will see later in this course, such networks are referred to as ***"scale-free"*** and they are likely to have nodes with much larger degree than the average degree.

### Food for Thought

Show why the previous two distributions give straight lines when we plot them in a log-linear and log-log scale, respectively. Also show that, with the exponential degree distribution, the probability to see nodes with degree more than 10 times the average is about 1/10000 of the probability to see nodes with higher degree than the average. On the other hand, with the power-law distribution, the probability to see nodes with degree more than 10 times the average is 1/100 of the probability to see nodes with higher degree than the average (when $\alpha = 2$).

## 04 — Example: Degree Distribution of a Sex-Contact Network

### Resource

- [Simulated Epidemics in an Empirical Spatiotemporal Network of 50,185 Sexual Contacts](http://www.ploscompbiol.org/article/info%3Adoi%2F10.1371%2Fjournal.pcbi.1001109#s2). Luis E. C. Rocha, Fredrik Liljeros, Petter Holme (2011). See [[readings/Simulated Epidemics in an Empirical Spatiotemporal.pdf|local copy]].

### Video: An Example — Degree Distribution of a Sex-Contact Network

[[sections/04-example-sex-contact-network.mp4]]

Video URL: https://mediaspace.gatech.edu/media/t/1_rhkbd9vv

| Text |
|------|
| Human sexual contacts for a spatio temporal network, the underlying structure over which |
| sexually transmitted infections, or STIs, spread. By understanding the structure of this |
| network, we can better understand the dynamics of such infections. Here we show you some |
| results from a bipartite network between sex buyers and their escorts. The nodes in this |
| bipartite network are either male sex buyers, about 17,000 of them. Or female escorts |
| about 10,000 of them and edge between them the nodes sexual intercourse between a male |
| sex buyer and the female escort. The average degree of the male buyers is about five. The |
| average escort degree is about 7.6 and the maximum degree of any node is actually 615. |
| What you see in these plots is the probability density functions of the node degrees, |
| either for male clients or for female escorts, the plots at the lower part so the |
| complimentary cumulative distribution functions of the degrees for this network in log |
| log scale. These plots as you can see, they are not straight lines of course, but if we |
| focus on the part of the distribution that extends up to a probability of about 10 to the |
| minus three 0.001. They can be approximated as straight lines. Note that, even though 90% |
| of the escorts have fewer than 20 clients there is a small number of hub escorts that |
| have a significantly larger number of clients. As we will see later in this course, sets |
| nodes that have a very large degree can play a major role in such epidemics. |

## 05 — Friendship Paradox

### The Probability that a Random Edge Connects to a Node of Degree k

Let's start by deriving a simple fact that we will use repeatedly in this course.

Suppose that we pick a random edge in the network — and we randomly select one of the two end-points of that edge — *we refer to those end-points as the **stubs** of the edge*. What is the probability $q_k$ that a randomly chosen stub belongs to a node of degree $k$?

This is easy to answer when the degrees of connected nodes are independent.

$$q_k = (\text{number of nodes of degree } k) \times (\text{probability an edge connects to a specific node of degree } k) = \left(np_k\right)\left(\frac{k}{2m}\right) = \frac{kp_k}{\frac{2m}{n}} = \frac{kp_k}{\overline{k}}$$

Note that the probability that the randomly chosen stub connects to a node of degree $k$ is proportional to both $k$ and the probability that a node has degree $k$.

This means that, for nodes with degree $k > \overline{k}$, it is more likely to sample one of their stubs than the nodes themselves. The opposite is true for nodes with degree $k < \overline{k}$.

![[img/05-graph-stubs.png|600]]

Based on the previous derivation, we can now ask: *what is the expected value of a neighbor's degree?*

Note that we are not asking for the average degree of a node. Instead, we are interested in the average degree of a node's neighbor.

This is the same as the expected value of the degree of the node we select if we sample a random edge stub. Let's denote this expected value as $\overline{k_{nn}}$.

The derivation is as follows.

$$\overline{k_{nn}} = \sum_{k=0}^{\max\ degree} k \cdot q_k = \sum_k k\frac{kp_k}{\overline{k}} = \frac{\sum_k k^2 p_k}{\overline{k}} = \frac{\overline{k^2}}{\overline{k}} = \frac{\left(\overline{k}\right)^2 + \left(\sigma_k\right)^2}{\overline{k}} = \overline{k} + \frac{\sigma_k^2}{\overline{k}}$$

We can now give a mathematical statement of the friendship paradox: as long as the variance of the degree distribution is not zero, and given our assumption that neighboring nodes have independent degrees, the average neighbor's degree is higher than the average node degree.

The difference between the two expected values (i.e., $\sigma_k^2/\overline{k}$) increases with the variability of the degree distribution.

### Food for Thought

Can you explain in an intuitive way why the average neighbor's degree is larger than the average node degree, *as long as the degree variance is not zero?*

### Video: The Friendship Paradox

[[sections/05-friendship-paradox.mp4]]

Video URL: https://mediaspace.gatech.edu/media/t/1_sl5ixn0r

| Text |
|------|
| Here is a first interesting application of the degree distribution of a network. Have you |
| ever heard about the friendship paradox? The friendship paradox states informally that on |
| the average, our friends have more friends than us. If you have not heard about this |
| before, spend some time reflecting on this question about you and your friends. Do you |
| think it is true? A bit more formally, we will now show mathematically that given a |
| network the average neighboring node degree is higher than the average node degree in the |
| network. And as we will see shortly, this is through under quite general conditions. |

## 06 — Two Extreme Cases of The Friendship Paradox

![[img/06-two-extremes.png|600]]

Think of two extremes in terms of degree distribution: an infinitely large regular network in which all nodes have the same degree *(and thus the degree variance is 0)*, and an infinitely large star network with one hub node at the center and all peripheral nodes connecting only to the hub.

In the regular network, the degree variance is zero and the average neighbor's degree is not different than the average node degree.

In the star network, on the other hand, the degree variance diverges as $n$ increases, and so does the difference between the average node degree and the average neighbor degree.

### Food for Thought

Derive the second moment of the degree distribution for the star network as the size of the network tends to infinity.

## 07 — Application of Friendship Paradox in Immunization Strategies

### Video: Application of the Friendship Paradox

[[sections/07-application-friendship-paradox-immunization.mp4]]

Video URL: https://mediaspace.gatech.edu/media/t/1_ldqcxvp3

| Text |
|------|
| The friendship paradox is not just mathematically interesting. It also has interesting |
| practical applications. For instance, think of an epidemic in which a virus spreads from |
| person to person through a social network. Suppose that no one in the population has |
| natural immunity to this virus. Without any intervention, the virus will eventually |
| spread from patient zero, which you see on this slide as a red node, to everybody else, |
| and eventually everybody will get sick. What if there is a vaccine however? Who would you |
| choose to vaccinate based on this network? One option is to vaccinate everybody. Of |
| course, this is very difficult in practice and it may not even be possible when there is |
| only limited vaccine. Here in the visualization, we see that everybody is immunized and |
| so the only person that is sick is patient zero, the red node at the upper left. Another |
| option is to vaccinate people randomly. As you see in this slide, three of the members of |
| this population are immunized, they're shown with a blue color. Even in this case, a |
| large portion of the population can still get sick depending on the connections they have |
| in the network. Another option is to vaccinate the nodes with a highest degree. Say that |
| we have enough vaccine for three people in this network. Instead of selecting them |
| randomly, we can select the three nodes with the highest degree as shown in this |
| visualization. In that case, only one person in this example will get sick, denoted by B. |
| Even though this approach is very effective, it is also very hard to implement in |
| practice. There is a nice that such networks of interactions between people are rarely |
| known in their entirety or accurately. So what can we do if we do not have such a |
| complete network map? Here is an interesting vaccination strategy that is based on the |
| friendship paradox. It is referred to as acquaintance immunization. Instead of |
| vaccinating random people, we select few random individuals, and ask each of them to |
| identify his or her contact with a maximum number of connections. These contact may be a |
| sexual partner or other type of contact depending on the underlying virus. Now, based on |
| the friendship paradox, we know that even network includes some hubs. Then they are |
| probably connected to some of the randomly selected individuals we chose to survey. So in |
| this animation, at this point, we choose the random set of nodes v1, v2, v3. And we asked |
| each of them to identify the node with the highest number of connections. As you see, |
| node v1 points to the node u2, see has the highest number of connections according to v1. |
| Node v2 points to node v1, and node v3 also points to node, the u2. So in this case, we |
| would basically select the nodes u1 and u2 to vaccinate. After we do so, as you can see |
| in this animation, only the node B will get infected from node A. Everybody else will |
| stay healthy. |

## 08 — The G(n,p) model (ER Graphs)

Let's consider now the simplest random graph model and its degree distribution.

This model is referred to as $G(n, p)$ and it can be described as follows: the network has $n$ nodes and the probability that any two distinct nodes are connected with an undirected edge is $p$.

The model is also referred to as the Gilbert model, or sometimes the Erdős–Rényi (ER) model, from the last names of the mathematicians that first studied its properties in the late 1950s.

Note that the number of edges $m$ in the $G(n,p)$ is a random variable. The expected number of edges is $p \cdot \frac{n(n-1)}{2}$, the average node degree is $p \cdot (n-1)$, the density of the network is $p$ and the degree variance is $p \cdot (1-p) \cdot (n-1)$. These formulas assume that we do not allow self-edges.

The degree distribution of the $G(n,p)$ model follows the Binomial$(n-1,p)$ distribution because each node can be connected to $n-1$ other nodes with probability $p$.

Note that the $G(n,p)$ model does not necessarily create a connected network — we will return to this point a bit later.

Also, in the $G(n,p)$ model there are no correlations between the degrees of neighboring nodes. So, if we return to the friendship paradox, the average neighbor degree at a $G(n,p)$ network is $\overline{k_{nn}} = \overline{k} + (1-p)$ (using the Binomial distribution) — or $\overline{k_{nn}} = \overline{k} + 1$ (using the Poisson approximation when $p \ll 1$).

In other words, if we reach a node $v$ by following an edge from another node, the expected value of $v$'s degree is one more than the average node degree.

***Food-for-thought:*** Derive the previous expressions for the average neighbor degree with both the Binomial and Poisson degree distributions.

## 09 — Degree Distribution of G(n,p) Model

Here is a well-known fact that you may have learned in a probability course: the Binomial distribution can be approximated by the Poisson distribution as long as $p$ is much smaller than 1. In other words, this approximation is true for sparse networks in which the average degree $p \cdot (n-1)$ is much lower than the size of the network $n$. The Poisson distribution is described by:

$$p_k = e^{-\overline{k}} \cdot \frac{\overline{k}^{k}}{k!}, \quad k = 0, 1, 2, \ldots$$

$$\overline{k} = p \cdot (n-1) \qquad \sigma_k^2 = \overline{k}$$

Because of the $\frac{1}{k!}$ term, $p_k$ decreases with $k$ faster than exponentially.

You may ask, why use the Poisson approximation instead of the Binomial$(n-1,p)$ distribution?

The reason is simple: the Poisson distribution has a single parameter, which is the average node degree $\overline{k}$.

![[img/09-gnp-poisson-degree-dist.png|600]]

The visualization shows the degree distribution for a network in which the average degree is 50. As we increase the number of nodes $n$, we need to decrease the connection probability $p$ so that their product remains constant. Note that the Poisson distribution is a rather poor approximation for $n=100$ *(because the average node degree is half of $n$)* but it is excellent as long as $n$ is larger than 1000.

### Food for Thought

Try to derive mathematically the Poisson distribution from the Binomial distribution for the case that $p$ is much smaller than 1 and $n$ is large. If you cannot do it, refer to a textbook or online resource for help.

## 10 — Connected Components in G(n,p)

Clearly, there is no guarantee that the $G(n,p)$ model will give us a connected network. If $p$ is close to zero, the network may consist of many small components. So an important question is: **how large is the Largest Connected Component (LCC) of the $G(n,p)$ model?**

Here is an animation that shows a network with $n=1000$ nodes, as we increase the average node degree $\overline{k}$ (shown at the upper-left of the animation). Recall that the connection probability is approximately $p \approx \frac{\overline{k}}{n}$.

As you see, initially we have only small groups of connected nodes — typically just 2-3 nodes in every connected component.

After the first 5-10 seconds of the animation however, we start seeing larger and larger connected components. Most of them do not include any loops — they form tree topologies.

Gradually, however, as the average degree approaches the critical value of one, we start seeing some connected components that include loops.

Something interesting happens when the average degree exceeds one *(about 40 seconds after the start of the animation)*: the largest connected component (LCC), which is identified with a different color than the rest of the nodes, starts covering a significant fraction of all network nodes. It starts becoming a ***"giant component"***.

If you continue watching this animation until the end *(it takes about five minutes)*, you will see that this giant component gradually changes color from dark blue to light blue to yellow to red — the color *"temperature"* represents the fraction of nodes in the LCC. Eventually, all the nodes join the LCC when the average node degree is about 6 in this example.

## 11 — Size of LCC in G(n,p) as Function of p

We can derive the relation between $p$ and the size of the LCC as follows:

![[img/11-lcc-fixed-point.png|600]]

Suppose that $S$ is the probability that a node belongs in the LCC. Another way to think of $S$ is as the expected value of the fraction of network nodes that belong in the LCC.

Then, $\overline{S} = 1 - S$ is the probability that a node does NOT belong in the LCC.

That probability can be written as

$$\overline{S} = \left( (1-p) + p \cdot \overline{S} \right)^{n-1}$$

The first term refers to the case that a node $v$ is not connected to another node, while the second term refers to the case that $v$ is connected to another node that is **not** in the LCC.

Since $p = \frac{\overline{k}}{n-1}$, the last equation can be written as:

$$\overline{S} = \left( 1 - \frac{\overline{k}}{n-1}\left( 1 - \overline{S} \right) \right)^{n-1}$$

$$\ln\overline{S} = (n-1)\ln\left( 1 - \frac{\overline{k}}{n-1}\left( 1 - \overline{S} \right) \right) \approx -(n-1)\frac{\overline{k}}{n-1}\left( 1 - \overline{S} \right)$$

$$S = 1 - e^{-\overline{k}S}$$

The visualization shows the relation between the left and right sides of the previous equation, i.e., the relation between $S$ and $1 - e^{-\overline{k}S}$.

The equality is true when the function $y = 1 - e^{-\overline{k}S}$ crosses the diagonal $x = y$ line.

Note that the derivative of $y$ with respect to $S$ is approximately $\overline{k}$ when $S$ approaches 0.

So, if the average degree is larger than one, the function $y(S)$ starts above the diagonal. It has to cross the diagonal at a positive value of $S$ because the second derivative of $y(S)$ is negative. That crossing point is the solution of the equation $S = 1 - e^{-\overline{k}S}$. **This means that if the average degree is larger than one ($\overline{k} > 1$), the size of the LCC is $S > 0$.**

On the other hand, if the average node degree is less (or equal) than 1, the function $y(S)$ starts with a slope that is less (or equal) than 1, and it remains below the diagonal $y = x$ for positive $S$. This means that if the average node degree is less or equal than one, the average size of the LCC in a $G(n,p)$ network includes almost zero nodes.

![[img/11-phase-transition.png|600]]

The visualization shows how $S$ increases with the average node degree $\overline{k}$. Note how the LCC suddenly ***"explodes"*** when the average node degree is larger than 1. This is referred to as a *"phase transition"*. A phase transition that we are all familiar with is what happens to water when its temperature reaches the freezing or boiling temperature: the macroscopic state changes abruptly from liquid to solid or gas. Something similar happens with $G(n,p)$ when the average node degree exceeds the critical value $\overline{k} = 1$: the network suddenly acquires a *"giant connected component"* that includes a large fraction of all network nodes.

Note that the critical point corresponds to a connection probability of $p = \frac{\overline{k}}{n-1} \approx \frac{1}{n}$, because $\overline{k} = (n-1) \ast p$.

## 12 — When Does G(n,p) have a Single Connected Component?

Here is one more interesting question about the size of the LCC: **how large should $p$ (or $\overline{k}$) be so that the LCC covers all network nodes?**

Note that the previous derivation did not answer this question — it simply told us that there is a phase transition when $\overline{k} = 1$.

Suppose again that $S$ is the probability that a node belongs in the LCC.

Then, the probability that a node does NOT connect to ANY node in the LCC:

$$(1-p)^{S\,n} \approx (1-p)^{n}\ \text{if}\ S \approx 1$$

The expected number of nodes not connecting to LCC:

$$\overline{k_o} = n \cdot (1-p)^{n} = n\left( 1 - \frac{np}{n} \right)^{n} \approx n \cdot e^{-np}$$

Recall that $\left( 1 - \frac{x}{n} \right)^{n} \approx e^{-x}$ when $x \ll n$. So we assume at this point of the derivation that the network is sparse ($p \ll 1$).

If we set $\overline{k_o}$ to less than one node, we get that:

$$n \cdot e^{-np} \leq 1$$

$$-np \leq \ln\left( \frac{1}{n} \right) = -\ln n$$

$$p \geq \frac{\ln n}{n}$$

$$\overline{k} = np \geq \ln n$$

which means that when t**he average degree is higher than the natural logarithm of the network size ($\overline{k} > \ln n$)** we expect to have a single connected component.

## 13 — Degree Correlations

![[img/13-assortative-disassortative.png|600]]

We assumed throughout this lesson that the degree of a node does not depend on the degree of its neighbors. In other words, **we assumed that there are no degree correlations.**

Mathematically, if nodes $u$ and $v$ are connected, we have assumed that:

**Prob[degree($u$) = $k$ | degree($v$) = $k'$] = Prob[degree($u$) = $k$ | $u$ connects to another node]** $= q_k = p_k \cdot \frac{k}{\overline{k}}$

Note: this probability does not depend on the degree $k'$ of neighbor $v$. Such networks are referred to as **neutral**.

In general, however, there are correlations between the degrees of neighboring nodes, and they are described by the conditional probability distribution:

**P[$k'$ | $k$] = Prob[a neighbor of a $k$-degree node has degree $k'$]**

The expected value of this distribution is referred to as the **average nearest-neighbor degree $k_{nn}(k)$** of degree-$k$ nodes:

$$k_{nn}(k) = \sum_{k'} k' \cdot P\left( k' \mid k \right)$$

In a neutral network, we have already derived that $k_{nn}(k)$ is independent of $k$ (recall that we derived $k_{nn}(k) = \overline{k} + \frac{\sigma_k^2}{\overline{k}} = \overline{k}_{nn}$).

In most real networks, $k_{nn}(k)$ depends on $k$ and it shows an increasing or decreasing trend with $k$.

The network at the left shows an example in which small-degree nodes tend to connect with other small-degree nodes *(and similarly for high-degree nodes)*.

The network at the right shows an example of a network in which small-degree nodes tend to connect to high-degree nodes.

### Degree Correlation Example

![[img/13-knn-example.png|600]]

Here is an example: what is the average nearest neighbor degree of node $v$ in this network?

$$\overline{k_{nn}}\left(v\right) = \frac{1}{k\left(v\right)}\sum_{i=1}^{k\left(v\right)} k\left(u_i\right) = \frac{6+4+2+4}{4} = 4$$

To calculate $k_{nn}(k)$ we compute the average value of $k_{nn}(v)$ for all nodes $v$ with $k(v) = x$.

Then, we plot $k_{nn}(k)$ versus $k$, and examine whether that plot shows a statistically significant positive or negative trend.

## 14 — How to Measure Degree Correlations

One way to quantify the degree correlations in a network is by modeling *(i.e., approximating)* the relationship between the average nearest neighbor degree $k_{nn}(k)$ and the degree $k$ with a power-law of the form:

$$k_{nn}(k) \approx a \cdot k^{\mu}$$

Then, we can estimate the exponent $\mu$ from the data.

1) If $\mu > 0$, we say that the network is **Assortative**: higher-degree nodes tend to have higher-degree neighbors and lower-degree nodes tend to have lower-degree neighbors. Think of celebrities dating celebrities, and loners dating other loners.

2) If $\mu < 0$, we say that the network is **Disassortative**: higher-degree nodes tend to have lower-degree neighbors. Think of a computer network in which high-degree aggregation switches connect mostly to low-degree backbone routers.

3) If $\mu$ is statistically not significantly different from zero, we say that the network is **Neutral**.

**NOTE: There is an errata in the online Barabási textbook about this topic where the direction of assortative and disassortative are reversed. The interpretation of degree correlations on this lecture slide is correct.**

### Food for Thought

Suppose that instead of this power-law relation between $k_{nn}(k)$ and $k$ we had used a linear statistical model. How would you quantify degree correlations in that case?

**Hint**: How would you apply Pearson's correlation metric to quantify the correlation between degrees of adjacent nodes?

## 15 — Assortative, Neutral and Disassortative Networks

### Video: Assortative, Neutral and Disassortative Networks

[[sections/15-assortative-neutral-disassortative.mp4]]

Video URL: https://mediaspace.gatech.edu/media/t/1_hf2nly3m

| Text |
|------|
| Let's look at some examples of science degree correlation plots from real world networks. |
| The first network refers to the collaboration between a group of scientists, two nodes, |
| two scientists are connected if they have written at least one research paper together. |
| Notice that the data is quite noisy especially when the degree K is more than about 70. |
| The reason simply that we did not have a large enough sample of such nodes with large |
| degrees. Nevertheless, we clearly see a positive correlation between the degree K and the |
| degree of the nearest neighbor, which is shown in the y axis. If we model the data with a |
| power law relation, the exponent mu is approximately 0.37 in this case. We can use this |
| value to quantify and compare the sort of activity of different networks when the |
| estimate of mu is statistically significant. The second network refers to a portion of |
| the power grid in the United States. The data in this case does not support a strong |
| correlation between the degree K and the degree of the nearest neighbor. So it is safe to |
| assume that this network is what we call neutral. The third network refers to a metabolic |
| network where nodes here are metabolites. And they are connected. If two metabolites A |
| and B appear in the opposite sides of the same chemical reaction in a biological cell, |
| the data so a strong negative correlation in this case. But only if the nodes have degree |
| 5, 10, or higher. If we model the data with power law relation, the exponent mu is |
| approximately minus 0.76. This suggests that complex metabolites such as glucose, are |
| either synthesised through a process called anabolism. Or broken down into, through a |
| process called catabolism into a large number of simpler molecules such as carbon dioxide. |

## 16 — Lesson Summary

The main objective of this lesson was to explore the notion of ***"degree distribution"*** for a given network. The degree distribution is probably the first thing you will want to see for any network you encounter from now on. It gives you a quantitative and concise description of the network's connectivity in terms of average node degree, degree variability, common degree modes, presence of nodes with very high degrees, etc.

In this context, we also examined a number of related topics. First, the friendship paradox is an interesting example to illustrate the importance of degree variability. We also saw how the friendship paradox is applied in practice in vaccination strategies.

We also introduced $G(n,p)$, which is a fundamental model of random graphs — and something that we will use extensively as a baseline network from now on. We explained why the degree distribution of $G(n,p)$ networks can be approximated with the Poisson distribution, and analyzed mathematically the size of the largest connected component in such networks.

Obviously, the degree distribution does not tell the whole story about a network. For instance, we talked about networks with degree correlations. This is an important property that we cannot infer just by looking at the degree distribution. Instead, it requires us to think about the probability that two nodes are connected as a function of their degrees.

We will return to all of these concepts and refine them later in the course.

## 17 — Knowledge Check

See [[sections/17-knowledge-check.pdf|L3: Knowledge Check]].
