# Applications

| Text |
|------|
| Let us look now at a couple of applications of the previews network analysis metrics.  |
| First, we focus on the use of notes and centrality metrics, considering the Game of  |
| Thrones sequence of novels by George RR Martin. For each book of the saga, we can  |
| represent each character with a node, and the interactions between two characters with an  |
| edge. This data set has been created by the applied mathematician Andrew Beveridge and  |
| his students Jie Shan. In the data set, the edges are weighted based on the number of  |
| interactions between the two characters. But for most of this lesson, we will ignore the  |
| weights, and consider the unweighted and undirected network. Combining all the  |
| interactions across the five books, we get the network that is shown in the visualization  |
| at the left. For now you can ignore the colors, they refer to community, something that  |
| we will discuss later. Suppose you have not read the books or watch the TV show, how  |
| would you analyze this network to identify the most important characters? The table shows  |
| the top six characters according to five different centrality metrics we discussed  |
| earlier. The degree centrality, the weight degree or strength of a node. The eigenvector  |
| centrality, the PageRanks centrality, and the shortest path between the centrality. For  |
| its metric, the visualization shows the rank of the corresponding character according to  |
| that metric. As you see Jon is the leading character according to PageRank and between a  |
| centrality. While Tyrion is the leading character according to degree, strength, and  |
| eigenvector centrality. For those of you that are familiar with a story, this is not very  |
| surprising. Jon and Tyrion are probably the two most important characters in the saga,  |
| and they had many more interactions with almost all the important characters. Note that  |
| there can be quite a large variation in the rank of a node depending on the centrality  |
| metric. For instance, the Daenerys is rank three according to between the centrality, but  |
| 11th according to degree centrality. This may be because in the first few books, he did  |
| not have direct interactions with the rest of the characters in Westeros. Finally, let us  |
| look at an application of the Tao core concept that was introduced earlier in this  |
| lesson. Recall that C.elegans is a microscopic worm, and it's a dire brain consists only  |
| of about 300 neurons. Additionally, the wiring diagram of those neurons is fully mapped.  |
| So we know all the chemical and electrical synopsis between the neurons of C elegans.  |
| Some neurons are sensory, meaning that they are directly connected to sensory inputs and  |
| they deliver information from the outside world to the brain. For example, if the worm  |
| smells odors or it is touched at certain body parts, specific sensory neurons will fire.  |
| Other cells are motor neurons, and they are directly connected to the muscles of this  |
| microscopic organism causing motion, and all other body actions. There are also some  |
| interneurons that are transforming the sensory input to output. In a recent study, we  |
| analyzed this neural network considering all feed forward paths from sensory to motor  |
| neurons. This set of paths was then analyzed using the Tao core algorithm we discussed  |
| earlier in this lesson. It turns out that a small set of about ten interneurons that you  |
| see here is sufficient to cover 90% of all sensory to motor paths in the brain of  |
| C.elegans. This list of neurons is shown here. Most of these inter neurons were  |
| previously known to neuroscientists as important commands neurons based on ablation  |
| studies or circuit level studies. The new analysis based on the Tao core method provides  |
| a different way to understand that all of these ten inter neurons. Their activity as a  |
| group, compresses all the information provided by the about 100 sensory neurons to a much  |
| lower dimensional space, which is represented by the activity of only 10 cells. Then this  |
| compressed representation is used to drive all the output behavior secrets of the  |
| organism that involve about 100 in motor neurons. In other words, it appears that  |
| C.elegans deploys an encoder/decoder architecture, similar to the architecture of deep  |
| artificial neural nets that first reduce the dimensionality of their inputs before  |
| computing typically much larger dimensionality output vector. |
