# Lesson 1 — What is Network Science?

> Source: Canvas — CS-7280-O01, OAN (Summer 2026)

---

## 00 — Lesson Overview

### Video: Lesson One Overview

[[00-lesson-overview.mp4]]

Video URL: https://mediaspace.gatech.edu/media/t/1_24q5793w

| Text |
|------|
| The objective of this lesson is to introduce you to the field of network science. First,  |
| we will define what network science means. Then we will look at several examples of  |
| complex systems that can be studied using the tools of network science and be introduced  |
| to a number of important problems in this discipline. Finally, we will briefly review the  |
| history of this new field. |


### Learning Objectives

Students will be able to:

- Define "*network science*"
- Understand its history and connections with other disciplines
- Identify some network science applications

### Required and Recommended Reading

**Required Reading**

- Chapter-1 from A-L. Barabási, [Network Science](https://networksciencebook.com/), 2015.

**Recommended Reading**

Read at least one of the following papers, depending on your interests:

- Networks in Epidemiology: [An Integrated Modeling Environment to Study the Co-evolution of Networks, Individual Behavior and Epidemics](https://onlinelibrary.wiley.com/doi/epdf/10.1609/aimag.v31i1.2283) by Chris Barrett et al.
- Networks in Biology: [Network Inference, Analysis, and Modeling in Systems Biology](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC2174897) by Reka Albert
- Networks in Neuroscience: [Complex brain networks: graph theoretical analysis of structural and functional systems](http://www.nature.com/nrn/journal/v10/n3/full/nrn2575.html) by Ed Bullmore and Olaf Sporns
- Networks in Social Science: [Network Analysis in the Social Sciences](https://www.science.org/doi/abs/10.1126/science.1165821) by Stephen Borgatti et al.
- Networks in Economics: [Economic Networks: The New Challenges](https://www.sg.ethz.ch/publications/2009/schweitzer2009economic-networks-the) by Frank Schweitzer et al.
- Networks in Ecology: [Networks in Ecology](https://www.sciencedirect.com/science/article/abs/pii/S1439179107000576?via%3Dihub) by Jordi Bascompte
- Networks and the Internet: [Network Topologies: Inference, Modelling and Generation](http://www.ee.ucl.ac.uk/~mrio/papers/hamedjrnl_camera.pdf) by Hamed Haddadi et al.

### Assignments

- L1: Knowledge Check
- L1: Quiz One

---

## 01 — What Is Network Science?

Let's first start with the obvious question: *What is network science?*

One possible definition is the following:

*The study of complex systems focusing on their architecture, i.e., on the network, or graph, that shows how the system components are interconnected.*

In other words, Network Science or NetSci focuses on a **network representation of a system** that shows how the system components are interconnected. To understand this definition further, let's first explore the concept of *Complex Systems.*

---

## 02 — Complex Systems

![[02-four-complex-systems.png|600]]

The image above shows a microprocessor, a human brain, an online social network, and a fighter jet. On the surface, you may think that these systems have nothing in common!

However, they all have some common fundamental properties:

1. Each of them consists of many autonomous parts, or modules – in the same way, that a large puzzle consists of many little pieces. The microprocessor, for example, consists of mostly transistors and interconnects. The brain consists of various cell types, including excitatory neurons, inhibitory neurons, glial cells, etc.
2. The parts of each system are not connected randomly or in any other trivial manner – on the contrary, the system only works if the connections between the parts are highly specific (for example, we would not expect an electronic device to work if its transistors were randomly connected). These interconnections between the system components define the architecture of the system – or in other words, the network representation of the system.
3. The interactions between connected parts are also non-trivial. A trivial interaction would be, mathematically, a linear relation between the activity of two parts. On the contrary, as we will discuss later in the course, in all interesting systems at least, these interactions are non-linear.

**To summarize, Complex Systems have:**

- Many and heterogeneous components
- Components that interact with each other through a *(non-trivial)* network
- Non-linear interactions between components

Next, we'll discuss Trivial Networks versus Complex Networks.

---

## 03 — Trivial Networks Versus Complex Networks

![[03-trivial-vs-complex-networks.png|600]]

*Image Source: [Local Patterns to Global Architectures: Influences of Network Topology on Human Learning. Karuza, Thompson-Schill, Bassett; 2016](https://www.cell.com/trends/cognitive-sciences/fulltext/S1364-6613(16)30071-7)*

Trivial Networks also known as regular or random networks differ significantly from complex networks as the image above shows.

***"Regular networks"*** are a large family of networks that have been studied extensively by mathematicians over the last couple of centuries. Regular networks such as rings, cliques, lattices, etc, have the same interconnection pattern, the same structure, at all nodes.

The example shown at the left in the image above is a regular network in which every node connects to four other nodes.

Another well-studied class of networks in graph theory is that of ***"Random networks"***. Here, the connections between nodes are determined randomly. In the simplest model, each pair of nodes is connected with the same probability.

In practice, most technological, biological and information systems do ***NOT*** have a regular or random network architecture. Instead, their architecture is highly specific, resulting in interconnection patterns that are highly variable across nodes.

For example, the network in the middle has several interesting properties that would not be expected if the network was randomly *"wired"*: note that there are three major clusters of nodes, few nodes have a much larger number of connections than others, and there are many connected three-node groups.

A major difference between network science and graph theory is that the former is an applied data-science discipline that focuses on complex networks encountered in real-world systems.

Graph theory, on the other hand, is a mathematical field that focuses mostly on regular and random graphs. We will return to the connection between these two disciplines later in this lesson.

---

## 04 — Example: The Brain of the C.elegans Worm

![[04-celegans-brain.png|600]]

*(Image Source: **[wormwiring.org](https://wormwiring.org/)**)*

To understand the relationship between a complex system and its network representation, let's focus on a microscopic worm called C.elegans.

This amazing organism, which is *about 1mm in length*, has roughly only 300 neurons in its neural system. Still, it can move in different ways, react to touch, mate, sense chemical odors, and respond to food versus toxins, etc.

Each dot represents a neuron, and the location of every neuron at the worm's body is shown at the top right. The connections between neurons, at the level of individual synapses, have been mapped using electron micrographs of tiny slices of the worm's body.

The network on the right in the image shows each neuron as a node and each connection between two neurons as an edge between the corresponding two nodes. Do not worry about the different colors for now – we will discuss this network again later in the course. The important point, for now, is that network science maps this highly complex living system into a graph -- an abstraction that we can analyze mathematically and computationally to ask a number of important questions about the organization of this neural system.

Note that this mapping from an actual system to a graph representation is only a model, and so it discards some information that the modeler views as non-essential. For instance, the network representation does not show in this example if a neuron is excitatory or inhibitory -- or whether these connections remain the same during the worm's lifetime.

**So it is always important to ask:** *does the network representation of a given system provide sufficient detail to answer the questions we are really interested in about that system?*

---

## 05 — The Main Premise

We can now state the main idea, the main premise, of network science:

*The network architecture of a system provides valuable information about the system's function, capabilities, resilience, evolution, etc.*

*In other words, even if we don't know every little detail about a system and its components, simply knowing the map or "wiring diagram" that shows how the different system components are interconnected provides sufficient information to answer a lot of important questions about that system.*

*Or, if our goal is to design a new system (rather than analyze an existing system), network science suggests that we should first start from its network representation, and only when that is completely done, move to lower-level design and implementation.*

![[05-network-architectures.png|600]]

Above, is an example to illustrate the previous point. *(Image Source: [techiereader.com](https://techiereader.com/category/networking))*

Even if you know nothing about the underlying system, what would you say about its efficiency and resilience under each of the following architectures?

Suppose that we are to design a communication system of some sort that will interconnect 6 sites. The first question is: what should be the network architecture? This figure shows several options. For example, the Ring architecture provides two disjoint paths between every pair of nodes. The Line, Tree, and Star architectures require the fewest number of links but they are highly vulnerable when certain nodes or edges fail. The Fully Connected architecture requires the highest number of links but it also provides the most direct *(and typically faster)* and resilient communication. The Mesh architecture provides a trade-off between all previous properties.

---

## 06 — Examples of Systems Studied by Network Scientists

In the next few pages, I would like to give you some examples of the problems we will study during the semester in this course. The description will be high-level as I only want to give you a taste of what is coming up next.

### Video: Examples of Systems Studied by Network Scientists — Part 1

[[06-examples-of-systems-part-1.mp4]]

Video URL: https://mediaspace.gatech.edu/media/t/1_eodmaw1x

### Video: Examples of Systems Studied by Network Scientists — Part 2

[[06-examples-of-systems-part-2.mp4]]

Video URL: https://mediaspace.gatech.edu/media/t/1_hn4blvyo

#### Examples of Systems Studied by Network Scientists — Part 1

| Text |
|------|
| Here's an example of a transportation network. So in the urban and the rural interstate  |
| highways, and other major highways in the US, the nodes in such a network could be all  |
| junctions or entry, exit points on a highway, while the edges can be the highway segments  |
| between such points. Note that the network of this type would typically have weighted  |
| edges, meaning that each edge would be associated with a number showing its capacity. For  |
| example, the number of lanes at that highway segment. Here is another transportation  |
| network example, this time for the direct flights of delta airlines in North America.  |
| This network would also be weighted, even though the weights are not shown in this  |
| visualization, with the weight of each edge being the number of available seats in all  |
| flights between the corresponding two airports on a daily basis. You can actually find  |
| such data for every airline through the Bureau of Transportation Statistics, which is  |
| part of the US Department of Transportation. See the link below this video. Here is an  |
| example of a computer network used in many data centers, referred to as the Fat Tree  |
| Topology. An important difference in this kind of graph representation is that we need to  |
| consider that not all nodes are of the same type. Some are servers, some are access  |
| switches, aggregation switches, our core switches. This difference means that each node  |
| in this graph is associated with a different computation or communication capacity. We  |
| should be careful to not ignore such heterogeneity in the nature of nodes or edges.  |
| Otherwise, it is possible to reach completely wrong conclusions. Let's move now from  |
| technological to human or social networks. In these networks, the nodes are typically  |
| specific individuals, and the edges represent different types of relation or contact. For  |
| instance, this figure is based on data from a very interesting study at the high school.  |
| 800 students were asked whether they had sexual relations during the past six months with  |
| another student at the same school. The network shows only those individuals that had at  |
| least one such relation in the given time period. Note that the network in this case does  |
| not consist of a connected graph. There are several connected components, with one of  |
| them at the top left being much larger than the others. This is common in most real-world  |
| networks. There may be more than one connected components, but typically, one of them  |
| covers the majority of the nodes. Note that most nodes have a small number of  |
| connections. For example, there are 63 pairs of nodes that do not connect to anyone else.  |
| But there are also few nodes with a much larger number of connections. This heterogeneity  |
| is a common property of many real-world networks. Online social networks have transformed  |
| our lives in the last 15 years or so. Here you see a small portion of the Twitter  |
| network, showing the connections between a number of poker players. In Twitter, a user  |
| can choose to follow another user. This means that the edges in the network are directed  |
| from one node to another. Of course, we can also have bi-directional edges, when two  |
| people follow each other. By the way, social networking is not a human invention. A large  |
| number of species create complex and dynamic social networks. This network refers to 62  |
| dolphins that were monitored for a period of about seven years. Two individuals are  |
| connected if they spent significant amount of time swimming together. The researchers  |
| that first performed this study noticed two strongly formed communities, the blue and the  |
| red. And a more weakly formed community, the green, that often interacts with both of the  |
| blue and red communities. The dolphins shown as black dots were not included in the  |
| original data analysis. The blue dashed line represents how a community detection  |
| algorithm would separate the dolphins into two groups without any information about the  |
| color of each node. Note that the algorithm is doing a pretty good job separating the  |
| blue and red communities, and it also suggests what group the black nodes most likely  |
| belong to. Networks sometimes refer to the exchange of products, materials, or just  |
| money. Such networks are viable in the field of economics and finance. The networks here  |
| show three different snapshots from 1995 to 2011, showing the trade volume between  |
| different countries, only the countries with the largest trade values. The visualization  |
| does not show numbers, but the edges are in fact directed and weighted showing the total  |
| trade volume from country x to country y during that year. This is a good example of a  |
| dynamic network, a network the changes over time. Note how much denser the network has  |
| gradually become. You can also see many other interesting changes, such as the major  |
| shift of China from a peripheral to a central role in the world trade network. If you  |
| want to analyze this data yourself, they are publicly available at the world trade  |
| organization link shown below. |

#### Examples of Systems Studied by Network Scientists — Part 2

| Text |
|------|
| Let's now switch to biological systems. There are several mechanisms in a living cell  |
| that depend on network interactions rather than individual chemical reactions or  |
| molecules. Most of the functions of a biological cell are performed through proteins. You  |
| can think of proteins as Lego pieces of specific shape and size that can interact with  |
| other proteins to perform a certain function, such as signal transduction, transport of  |
| other proteins or DNA transcription. The set of all possible interactions between protein  |
| pairs in a cell forms the protein-protein interaction, or PPI network of that cell. This  |
| network is extremely important, not only in understanding how the cell performs its  |
| function, but also to understand diseases in which one or more proteins does not fold  |
| properly, such as Alzheimer's, ALS or sickle cell disease. Additionally, PPI networks are  |
| instrumental in designing drugs that target specific viruses or other pathogens. This  |
| figure shows the PPI network of a single cell organism called fission yeast, and it  |
| consists of about 3,400 proteins and the 37,000 in directions. The different colored  |
| clusters in the network correspond to specific biological functions. As you can see, most  |
| functions are performed by groups of highly interconnected proteins. But there are also  |
| many proteins that bridge those clusters, contributing in more than one biological  |
| function. Ecologists also rely on networks to represent the interactions between species  |
| in an ecosystem. These interactions can take many forms, but in the simplest case we can  |
| consider only trophic links. In other words, who is eating what? The network in this  |
| visualization shows with the plants as green nodes in the center and crops in light  |
| green. It's type of consumer species at the periphery of the circle has a unique color.  |
| Note that some of the consumers eat both plants and animals. Such networks are crucial in  |
| predicting the effect of human interventions, herbicides, etc. The brain is also a system  |
| that is actively studied as a network, both at the level of individual neurons and at the  |
| lower spatial resolution at the level of brain regions. This figure shows a sketch of two  |
| neurons that connect through a synapses. When the left neuron, called pre-synaptic, fires  |
| it generates an action potential, in other words. The receiving neuron at the right will  |
| get depolarized and may also generate an action potential. Note that the connection is  |
| directed and weighted by the number and strength of the corresponding synapses. Our brain  |
| is nothing but a huge network of interconnected neurons. The human brain includes about  |
| 86 billion neurons and more than 100 trillion synapses, a huge network indeed. But it is  |
| important to pause for a moment and consider that all our impressive capabilities and  |
| fallacies are generated not by the complexity of individual neurons, but by the  |
| complexity of the network that interconnects those neurons. The neurons in the human  |
| brain are practically the same cells as the neurons in any other animal. What makes us  |
| humans, rather than flies or cats, is the network within our skull. As mentioned earlier  |
| in this lesson, we know the complete neural network of a few species, such as the  |
| microscopic worm, C-elegans. This visualization shows neurons with three different  |
| colors. Red for sensory neurons providing input to a neural system. Green for motor  |
| neurons generating output action by connecting to muscles. And blue for interneurons  |
| computing the intermediate level functions. It is extremely unlikely that we will have  |
| similar maps for the entire human brain in the near future. Instead, the human brain  |
| network is usually started at the courser level of spacial resolution using magnetic  |
| resonance imaging, or MRI, which is a non-invasive neuro imaging technology. Diffusion  |
| weighted MRI provides maps showing how different brain regions, down to a voxel dimension  |
| of about one millimeter, are connected to each other. These anatomical connections can be  |
| inferred using some very interesting algorithms that perform tractography and they allow  |
| us to create structural brain networks, as shown in the upper part of the figure.  |
| Functional MRI, or fMRI, on the other hand, provides a time series for its brain region  |
| showing how active that region is as a function of time. This depends, of course, on the  |
| cognitive task that the subject performs during the MRI scan. The spatio temporal  |
| correlations between different brain regions allows us to construct functional brain  |
| regions, as shown at the lower part of the figure. We will discuss in more technical  |
| detail how to infer and analyze functional networks derived from spatiotemporal data  |
| later in the course. |

### Source research articles for the images in these videos

- [Chains of Affection: The Structure of Adolescent Romantic and Sexual Networks](https://www.cis.upenn.edu/~mkearns/teaching/NetworkedLife/teensex.pdf)
- [Rise of China in the International Trade Network: A Community Core Detection Approach](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4138169)
- [Predicting the Fission Yeast Protein Interaction Network](https://pdfs.semanticscholar.org/0595/6042c6bd23eb49b5071964ce2d04edb26921.pdf)
- [Networking Our Way to Better Ecosystem Service Provision](https://www.sciencedirect.com/science/article/pii/S0169534715003006)
- [Influence of fake news in Twitter during the 2016 US presidential election](https://www.nature.com/articles/s41467-018-07761-2)

**Also, some images are copied from the following online sources:**

- [Wireless Data Center with Millimeter Wave Network](https://ieeexplore.ieee.org/document/5684121)
- [Data visualization for social network analysis](https://cambridge-intelligence.com/use-cases/social-networks/)
- [The bottlenose dolphin community of Doubtful Sound features a large proportion of long-lasting associations](https://link.springer.com/article/10.1007/s00265-003-0651-y)
- [The synapse, Khan Academy](https://www.khanacademy.org/science/biology/human-biology/neuron-nervous-system/a/the-synapse)
- [Action potentials and synapses, The University of Queensland](https://qbi.uq.edu.au/brain-basics/brain/brain-physiology/action-potentials-and-synapses)
- [Alterations in Brain Network Topology and Structural-Functional Connectome Coupling Relate to Cognitive Impairment](https://www.frontiersin.org/articles/10.3389/fnagi.2018.00404/full)
- [The Measurement Standard, Carma](https://persiababylonia.org/archives/methods/social-network-analysis-and-cuneiform-archives/)
- [Schizophrenia interactome with 504 novel protein–protein interactions](https://www.nature.com/articles/npjschz201612)

---

## 07 — Network Centrality

![[07-coauthorship-network.png|600]]

Above is an image that shows the co-authorship network for a set of Network Science researchers: each node represents a researcher and two nodes are connected if they have published at least one paper together. *(Image Source: [University of Michigan](http://www-personal.umich.edu/~mejn/centrality/labeled.png))*

A very common question in network science is: given a network representation of a system, which are the most important modules or nodes? Or, which are the most important connections or edges?

Of course, this depends on what we mean by "important" – and there are several different metrics that quantify the "centrality" of nodes and edges.

Sometimes we want to identify nodes and edges that are very central in the sense that most pairs of other nodes communicate through them.

Or, nodes and edges that, if removed, will cause the largest disruption in the underlying network.

![[07-got-centrality.png|600]]

For example, the image above refers to the characters of the third Game of Thrones novel, called ***"A storm of swords"***. *(Image Source: The Measurement Standard, Carma)*

Two nodes are connected if the corresponding two characters interacted in that novel, and the weight of the edge represents the length of that interaction.

Two different node centrality metrics are visualized in this figure. The size of the node refers to a centrality metric called PageRank – it is the same metric that was used by Google in their first web search engine. The PageRank value of a node v does not depend simply on how many other nodes point to v, but also how large their PageRank value is and how many other nodes they point to.

The second centrality metric refers to a centrality metric called "Betweenness" and it is shown by the size of the node's label. The Betweenness centrality of a node v relates to the number of shortest paths that traverse node v, considering the shortest paths across all node pairs.

Both metrics suggest that Tyrion and Jon are the most central characters in that novel, even though they were not interacting yet.

### Source Links

- [Finding community structure in networks using the eigenvectors of matrices](https://arxiv.org/abs/physics/0605087)

---

## 08 — Communities (Modules) in Networks

![[08-communities.png|600]]

Another important problem in Network Science is to discover Communities – in other words, clusters of highly interconnected nodes. The density of the connections between nodes of the same community is much larger than the density of the connections between nodes of different communities.

![[08-got-communities.png|600]]

Returning to the previous Game of Thrones visualization, each color represents a different community – with a total of 7 communities of different sizes.

For those of you that are familiar with the book or TV show *(mostly seasons 3 and 4)*, these communities make a lot of sense. Up to that point in the story, Daenerys, for instance, was mostly interacting with the Dothrakis and with Barristan, while Jon was mostly interacting with characters at Castle Black.

There are many algorithms for Community Detection – and some of them are able to identify nodes that participate in more than one community. We will discuss such algorithms later in the course.

---

## 09 — Dynamics of Networks

An important component of Network Science is the focus on Dynamic Networks – systems that change over time through natural evolution, growth or other dynamic rewiring processes.

For example, the brain's neural network is changing dramatically during adolescence – but more recent research in neuroscience shows that brain connections also change when people learn something new or even when they meditate.

![[09-dynamic-communities.png|600]]

The image above shows how the community structure of a network may be changing over time. *(Image Source: [The University of Florida](http://www.cise.ufl.edu/~tdinh/))*

Note that the white and red communities are gradually absorbed by the blue and the green community gradually collapses.

We will study algorithms that can detect and quantify such dynamic processes in networks.

Another important problem in Network Science is the study of Dynamic Processes on Networks. Here, the network structure remains the same – but there is a dynamic process that is gradually unfolding on that network.

For example, the process may be an epidemic that spreads through an underlying social network.

For certain viruses, such as HIV, the state of each human can be one of the following: healthy but susceptible to the virus, infected by the virus but not yet sick, or sick (*symptomatic*).

### Video: Computer Simulation of the Spread of a Pandemic

[[09-dynamics-of-networks.mp4]]

Video URL: https://www.youtube.com/watch?v=mm2u9RKwgsY

> [!NOTE] This YouTube video has no captions available, so no transcript is included.

The **video above** shows a simulation of the spread of the H1N1 virus over the global air transportation network. The H1N1 outbreak started in Mexico in 2009 and it quickly spread throughout the world mostly through air transportation.

An important question in Network Science: how does the structure of the underlying network affect the spread of such epidemics?

As we will see later in the course, certain network properties enhance the spread of epidemics to the point that they can become pandemics before any intervention is possible. The only way to prevent such pandemics is through immunizations when they are available.

---

## 10 — Influence and Cascade Phenomena

The dynamic processes that take place on a network are often not physical. For example, ideas, opinions, and other social trends and hypes can also spread through networks – especially over online social networks.

We will study such influence or "information contagion" phenomena in the context of mostly Facebook and Twitter.

![[10-fake-news-twitter.png|600]]

For example, the image above comes from a recent study focusing on the effect of misinformation *(known as "fake news")* on Twitter in the 2016 US Presidential Elections. *(Image Source: [Bovet, A., Makse, H.A. Influence of fake news in Twitter during the 2016 US presidential election. Nat Commun 10, 7 (2019)](https://www.nature.com/articles/s41467-018-07761-2))*

The study used network science to identify the most influential spreaders of fake news as well as traditional news.

An important but still open research question is whether it is possible to develop algorithms that can identify influential spreaders of false information in real-time and block them.

### Source Links

- [Influence of fake news in Twitter during the 2016 US presidential election](https://www.nature.com/articles/s41467-018-07761-2)

---

## 11 — Machine Learning and Network Science

We will also study problems at the intersection of Network Science and Machine Learning.

As you probably know, Machine Learning generates statistical models from data and then uses these models in classification, regression, clustering, and other similar tasks.

Network Science has contributed to this field by focusing on graph models – statistical models of static or dynamic networks that can capture the important properties of real-world networks in a parsimonious manner.

![[11-schizophrenia-interactome.png|600]]

The image above comes from a recent research paper about schizophrenia. *(Image Source: [Ganapathiraju, M., Thahir, M., Handen, A. et al. Schizophrenia interactome with 504 novel protein–protein interactions. npj Schizophr 2, 16012 (2016)](https://www.nature.com/articles/npjschz201612))*

It shows the interactions between genes associated with schizophrenia, and drugs that target either specific genes/proteins or protein-protein interactions. Machine Learning models have been used to predict previously unknown interactions between drugs and genes.

The drugs are shown as round nodes in green, and genes as square nodes in dark blue, light blue or red. Nervous system drugs are shown as larger size green colored nodes compared with other drugs. Drugs that are in clinical trials for schizophrenia are labeled purple. You can explore the visualization interactively with the following link: [Schizophrenia interactome with 504 novel protein–protein interactions](https://www.nature.com/articles/npjschz201612/figures/6)

---

## 12 — The History of Network Science

Let's talk now, rather briefly, about the history of network science.

First, it is important to emphasize that the term "*network*" has been used for decades in different disciplines.

For example, computer scientists would use the term to refer exclusively to computer networks, sociologists have been studying social networks for more than 50 years, and of course, mathematicians have been studying graphs for more than two centuries.

So what is new in network science?

### The Roots of Network Science

Network Science certainly leveraged concepts and methods that were developed earlier in Graph Theory, Statistical Mechanics and Nonlinear Dynamics in Physics, Computer Science algorithms, Statistics and Machine Learning. The list below shows the key topics that each of these disciplines contributed to Network Science.

- **Graph theory:**
  - Study of abstract (*mostly static*) graphs
- **Statistical mechanics:**
  - Percolation, phase transitions
- **Nonlinear dynamics:**
  - Contagion models, threshold phenomena, synchronization
- **Graph algorithms:**
  - Network paths, clustering, centrality metrics
- **Statistics:**
  - Network sampling, network inference
- **Machine learning:**
  - Graph embeddings, node/edge classification, generative models
- **Theory of complex systems:**
  - Scaling, emergence

There are ***two main differences*** however between these disciplines and Network Science.

***First***, Network Science focuses on real-world networks and their properties – rather than on regular or random graphs, which are easier to analyze mathematically but not realistic. Most of the earlier work in graph theory or physics was assuming that networks have that kind of simple structure.

***Second***, Network Science provides a general framework to study complex networks independent of the specific application domain. This unified approach revealed that there are major similarities and universal properties in networks, independent of whether they represent social, biological or technological systems.

---

## 13 — The Birth of Network Science

***The birth of Network Science took place back in 1998 or 1999, with the publication of two very influential research papers.***

![[13-small-world.png|600]]

The ***first*** was the discovery by Watts and Strogatz of the Small-World property in real-world networks. Roughly speaking, this means that most node-pairs are close to each other, only within a small number of hops. You may have heard the term *"six degrees of separation"*, in the context of social networks, meaning that most people are connected with each other through a path of 6 *(or so)* acquaintances.

![[13-scale-free.png|600]]

A ***second*** influential paper was published in 1999 by two physicists, Barabási and Albert.

That paper showed that real-world networks are *"Scale Free"*. This means that the number of connections that a node has is highly skewed: most nodes have a very small number of connections but there are few nodes, referred to as hubs, that have a much larger number of connections. Mathematically speaking, the number of connections per node follows a power-law distribution – something that we will discuss extensively later in this course.

Barabási and Albert explained this general phenomenon based on a *"rich get richer"* property. As a network gradually grows, new nodes prefer to create links to more well-connected existing nodes, and so the latter become increasingly more powerful in terms of connectivity. This is referred to as *"preferential attachment"* – and we will study it in detail later.

### Source Links

- [Collective dynamics of 'small-world' networks](https://www.nature.com/articles/30918)
- [Emergence of Scaling in Random Networks](https://science.sciencemag.org/content/286/5439/509)

---

## 14 — Lesson Summary

### Video: Lesson One Summary

[[14-lesson-summary.mp4]]

Video URL: https://mediaspace.gatech.edu/media/t/1_4hf28qce

| Text |
|------|
| We have reached the end of this first lesson. We have covered a large number of topics  |
| for many different disciplines. Please do not be discouraged, if you have not fully  |
| understood the parts that relate to biology, neuroscience or other disciplines. My main  |
| goal was to give you example of systems that can be modeled and studied using the network  |
| abstraction. For the remainder of this course, we will be mostly dealing with algorithms,  |
| data and metrics, concepts that are quite familiar to graduate students in computer  |
| science. If you are intrigued about any of the systems we mentioned today, I strongly  |
| suggest you read research papers that are linked on the overview page as recommended  |
| reading. I will leave you with a high level talk by Albert Laszlo Barabasi, who is widely  |
| considered as the father of Network science. He is a charismatic speaker and I'm sure you  |
| will enjoy his TED talk about the important role of networks in biology. |


---

## 15 — TED Lecture: Albert-László Barabási

### Video: TED Lecture — Albert-László Barabási

[[15-ted-lecture-barabasi.mp4]]

Video URL: https://www.youtube.com/watch?v=10oQMHadGos

| Text |
|------|
| [Music] so in many ways a broken car is not so different from a disease when the engine  |
| is smoking and the lights don't come up there's a fundamental difference however between  |
| humans and cars if I can get my car to a mechanic I can be pretty certain that they can  |
| fix it which is much more than we can say about many of our diseases today so why can a  |
| mechanic with much less education and much less box than a doctor fix our C while our  |
| doctor often let us go with diseases persisting in our body well there are a number of  |
| things that actually the mechanic has that the doctors doesn't have right now first of  |
| all it got a parts list it has a blueprint telling us how the pieces connect together it  |
| has Diagnostics tools to figure out where the comp you know what which is broken and what  |
| is healthy and it has means essentially to replace the parts now let's think about it  |
| what which of these components are available to our doctor today well the good news is  |
| that they finally got the parts list that was the outcome of the Human Genome Project and  |
| when the human genome was actually mapped about 10 years ago we thought it's going to be  |
| easy from now from the parts we will have essentially the W Bonanza that we need to fix  |
| us humans but of course the reality is sinking we also real thought that these many  |
| pieces will eventually give us lots of drugs in 2001 or 20 000 the year before the Genome  |
| Project was unveiled the FDA approved about a 100 drugs per year we thought this number  |
| could only go up it could only just increase yet the reality is in kin the number of  |
| approved drugs essentially in the last 10 years went from 100 before the genome to about  |
| 20 per year in hindsight the reason is pretty clear it's not enough to have the parts  |
| list we also need to actually have the how the pieces fit together that is we should not  |
| look at this picture but rather we should be looking at how the wiring diagram of the car  |
| looks like how the wir diagram of the of our cells actually look like how the genes and  |
| the proteins and the metabolites link to each other forming a consistent Network because  |
| this network which I'm going to try to tell you today is really too key to understanding  |
| human diseases now the problem is that if you look at this map you soon realize that you  |
| know it looks completely random randomness certainly has the upper hand but down the line  |
| it is not I believe that there's a deep order behind behind this wiring diagram and  |
| understanding that order is the key to understand human diseases now I'm a physicist and  |
| the conventional wisdom is that a physicist I should be studying very big objects starts  |
| quazars or very tiny ones like the Hig Bon and quar yet about a decade ago my interest  |
| has turned to a completely different subject complex systems and networks and that's  |
| because our very existence depends on the successful functioning of systems and networks  |
| behind us and I also believe that the scientific challenges behind complex systems and  |
| networks are just as DS as behind quarks or quasars so I started looking at the structure  |
| of the internet telling us how many many uh computers are linked together by uh various  |
| cables I looked at the structure of the social network telling us how the society is  |
| wired together through many friendship and other linkages and eventually I started  |
| looking at the structure of the cell telling us you know how our genes and proteins link  |
| to each other into a coherent Network and through that path I arrived to human diseases a  |
| path that is really taken by physic IST now the fundamental question that really comes up  |
| from that is you know how do we think about diseases in the context of these very very  |
| complicated Network and from that let me turn to a map that we all understand probably  |
| the most famous map out there which is the map of Manhattan now in many ways Manhattan is  |
| rather different from a uh from a cell but let's for a moment carry with me and let's  |
| believe together that this is really not a map of myam but it's a map of the cell where  |
| the intersection show as notes are the genes and the proteins and the street segments  |
| that connect them corresponds to the interactions between them now down the line you know  |
| this is not so different from what happens in our cells the busy life of Manhattan very  |
| easily Maps into the crowded life of the cell where molecules interact with each other  |
| and recombine and transport and so on so there's lots of similarities on the surface  |
| between them and if we look in Manhattan we also realize that action is not uniformly  |
| spread within the city if you want to go for example a theater you don't go to any parts  |
| of Manhattan you would go to the Theater District because that's where most of the  |
| theaters are that's where the shows are if you want to buy an artwork you will not be  |
| actually going anywhere within the city but you would be going to the gallery District  |
| because there's one small region of the town that that has most of the highend Galleries  |
| and that's where most artwork is for sale the same is true in the cell you know its  |
| functions are not spread uniformly within the network but there are other Pockets within  |
| the network that are responsible for particular functions and their breakdown potential  |
| release to disease so the way you think about disease in the context of the network is to  |
| think that there are different regions that correspond to different diseases of this map  |
| so for example you could say that cancer stay somewhere around Wall Street and and  |
| bipolar disease would be somewhere around Time Square and you know if you think of asthma  |
| a respiratory disease it would be somewhere up next to the Washington Bridge you know  |
| where really Manhattan breeds his people and cars into New Jersey and the Bronx now under  |
| normal conditions Manhattan is full of traffic and you know that's how the cell looks  |
| like our normally but if we have defects some genes breaking down that corresponds to  |
| some of the intersections not working and soon enough we will get a very typical  |
| Manhattan disease a traffic jam this is again not so different from what happens in our  |
| cells because there are many different ways you can actually get the same phenotype in  |
| the same ways there are many different ways you can actually get a disease for example  |
| there was a famous study by Bert Wen Stein's Group which which uh sequenc about 300  |
| individuals who all had coloror cancer they had the same phenotype so therefore the  |
| expectation was that all of them would have probably the same mutations in the same genes  |
| yet the study showed that not only they didn't have the same set of mutations but the  |
| mutations were all in different groups of genes there were no two individuals who would  |
| be actually have the same genes exactly the same group of genes uh uh defected the only  |
| way to understand how is it possible that many different genes broken down in different  |
| combinations linked to the same disease is to think think in terms of Manhattan is to  |
| think in terms of disease module and to really have the wiring diagram of the disease  |
| module to understand you know the breakdown modes of the particular system now if we  |
| really believe that particular uh picture the next step for us is really to say how do we  |
| proceed from here and it's very easy get a map find the disease module and Drug it now of  |
| course you do realize there's a catch here and the catch of course is that unlike for  |
| Manhattan we don't have yet a map for the uh for the cells I mean we do but some of the  |
| maps we have are very incomplete for example the best protein interaction map we have  |
| right now believe we believe that has only 5% of the links that are supposed to be in our  |
| cells now having part five 5% of the links means that we're missing n 95% of the links  |
| and that has dramatic consequences on the system let me illustrate that on Manhattan  |
| let's go ahead and take 95% of Street segments and remove it from the map let's see what  |
| does it do to Manhattan and the consequence is obvious the network will be broken into  |
| tiny pieces and as a result the modules the Wall Street neighborhood and timec  |
| neighborhood that were clearly distinguishable before will be all over the map you you  |
| don't know anymore where your disease module is so what can we do then well first and  |
| foremost we must improve on our maps and that's what my colleague uh Mark Vidal does at  |
| Den Farber Cancer Institute who in the last 20 years has developed a whole series of  |
| automatic tools to systematically map the protein interactions within the cell one of the  |
| very important component of the cellular network as a result of his work in about a few  |
| years ago we got what we call the 5% map the one I referred to earlier this year he's  |
| about to unveil another landmark the 20% map of the human cell and if we let him to stay  |
| in truck actually he will do the fall Network he may take a decade or two to get to it  |
| but eventually you know with the effort of he and many others we will get a map but what  |
| until then should we just wait for for him to finish the work and the answer is well not  |
| really there's lots of things we can actually do using the existing Maps so this is how  |
| the map looks like right now this is all the interactions that we leave we believe should  |
| be actually in the cell and in order to understand where diseas is lying that what I'm  |
| going to do next is that I will go ahead and place on this map a particular disease in  |
| this case Asma Asma is a respiratory disease that leads in a coughing shortness of breath  |
| and many other symptoms and there has been a tremendous amount of research understanding  |
| the genetic origins of masma so therefore we know about 100 genes that are known to be  |
| associated with Asma so if we put them on the map and I'm showing them now here as purple  |
| notes then we would expect them they would be all together because they really should  |
| correspond to our disease module but they're not they're all over the map and the reason  |
| why there W the map is pretty clear because we are missing 95% of the interactions so the  |
| critical links that would really hold them together in one module are all gone they're  |
| not there yet so what is that we can do next well we can use the power of the network  |
| that they are really built into the network and try to figure out other genes who may  |
| also be involved in ASA who about whom we don't know yet and that's exactly what we did  |
| next we took this map and we run algorithm through that that really extract the  |
| information from this map and identify what you see in front of your eyes the osma module  |
| within the cell now if we know the Asma module from there we can uh understand the D  |
| disease mechanism the disease Pathways and one day can actually help us understand the  |
| drugs but this is not only true for Asma not only Asma is located well in within the  |
| network you can take some other diseases for example COPD and try to do the same thing  |
| COPD is often called a smoker's disease because smokers are at very high chance of  |
| getting it and has somewhat similar symptoms to asthma so not surprisingly the net it  |
| seems to be that the two modules are significantly overlapping and they're certainly in  |
| the same region of the network we do expect however to have other diseases that would  |
| been a completely different part of the network and what is crucial here is to understand  |
| that the relationship between these diseases to what degree they overlap and how they  |
| relate to each other is really crucial to understand you know what is you know what how  |
| how they relate to each other and whe whether they are similar or very different from  |
| each other so one way to look at it is to you know let look at the relationship between  |
| all diseases and that's what I'm showing you here here in the next slide every note  |
| corresponds to a uh to a particular disease and two diseases are connected to each other  |
| if they share a gene why would you do that well because if they share a gene then very  |
| likely their disease module overlaps and therefore they must be in the same region of the  |
| network and what is amazing about this map is that you see that there are links between  |
| completely apparently unrelated diseases which is telling us that if you really want to  |
| kind of treat two you have two diseases and you want to treat them today you may go to  |
| different doctors different hospitals different floors but down at the level of the cell  |
| they are not independent from each other they're connected because they're rooted in  |
| someh out in the same neighborhood so what this is telling us this diseasome map how we  |
| call it is that if we want to understand disease we should not be looking really at the  |
| you know what we normally look at but we should be really looking at the network within  |
| our cells this is the one that really matters this is the one that really should tell us  |
| how to classify diseases you know we probably got it fundamentally wrong it's not heart  |
| it's not Brains it's not kidneys you know sooner or later we must abandon this organ  |
| based description of the disease and turn to what really matter we should stop training  |
| cardiologist and and uh and neurologist and the rather the doctor of future really needs  |
| to become a bit of network list to understand where diseases are lying within that  |
| Network and how they relate to each other so I personally believe that we need a new  |
| medicine to truly execute the Paradigm change that genomics allowed us to really achieve  |
| I would call it Network medicine and I think it's really within the our footstep to  |
| really kind of do and Achieve that I also think that Network medicine will not only help  |
| us understand the mechanism disease but it will affect all aspects of hair care you know  |
| from the role of the environment all the way to how we actually deliver care to a  |
| particular patient so climbing back to our original question you know the good news is  |
| that doctors are increasingly letting many many of the tools that the car mechanics has  |
| today you know if you think about it the genomics provides the parts list metabolomics  |
| and proteomics provides diagnostic tools and gene therapy is really giving us the way to  |
| one day to replace the components with with the pieces that are not broken but a car  |
| mechanic would be useless without the blueprint and in the same way I believe that to  |
| truly understand diseases we need to give in the hands of our doctors the map now I'm a  |
| physicist and a network scientist I'm not a medical doctor hence I will never cure any of  |
| your diseases I can help however decipher the map the real Book of Life the book that is  |
| currently missing most of its pages but once we learn to read it we'll get much closer to  |
| the secret of life and curing disease thank you very [Applause] much |

