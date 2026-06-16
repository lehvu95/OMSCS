# Examples of Systems Studied by Network Scientists — Part 1

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

# Examples of Systems Studied by Network Scientists — Part 2

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
