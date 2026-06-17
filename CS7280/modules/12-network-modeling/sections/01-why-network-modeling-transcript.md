# Why Network Modeling?

| Text |
|------|
| Let's start with some fundamental questions. Why do we need network models? What can we  |
| use them in practice? Why to use models instead of the actual data that describe a real  |
| world network? For instance, consider these two networks. The network at the right  |
| relates to the human malaria parasite which kills 1 million people globally every year.  |
| We also saw the adjacency matrix of this network ordered so that the existence of three  |
| communities, the blue, the green and the red, are clearly shown. If we want to ask  |
| questions about this specific network, we can work with this data and not rely on any  |
| model. What do we want, however, to use this data to ask more general questions about  |
| other parasites or about larger or smaller instances of this network? The figure at the  |
| left shows a network model. It also has three communities. This is a stochastic block  |
| matrix model and to describe it, we simply need to specify the number of communities, the  |
| size of its community and the probabilities of intra-community edges and inter-community  |
| edges. We can choose this parameter so that this model produces networks that are similar  |
| structurally with the malaria network we see at the right. Or we can use this model to  |
| create smaller or larger networks than the malaria network but still with three  |
| communities. Or we can use this model to generate hundreds of network instances, all of  |
| them having the same size and edge density, the same number of communities, but different  |
| topology. So when can we use such an abstract network model instead of the data that  |
| specify a given network? A model allows us to describe the given network in a  |
| parsimonious manner with fewer parameters than having to specify the complete adjacency  |
| matrix. A model also allows us to create an ensemble of many network instances, all of  |
| them having the same characteristics. With a model we can examine various network  |
| properties and dynamic behaviors if the network was smaller, larger, denser and so on.  |
| Also when working with noisy data we can infer whether some of the links in the given  |
| network are missing or they do not actually exist using a model. Finally if the model is  |
| mechanistic it can provide a plausible explanation of how the network came to be in its  |
| current structure. There are also many other reasons to use network models that are often  |
| application specific. |
