# Application: Polypharmacy

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
