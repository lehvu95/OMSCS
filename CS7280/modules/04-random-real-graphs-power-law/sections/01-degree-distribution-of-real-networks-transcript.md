# Degree Distribution of Real Networks

| Text |
|------|
| For many years, scientists used to think that real world networks can be modeled as  |
| random Erdős–Rényi graphs. As you know from less than three, such networks follow the  |
| binomial degree distribution, which can be approximated by the Poisson distribution. An  |
| important discovery in the history of network science came in the late 90s, when several  |
| researchers observed that real networks are very different. Their degree distribution is  |
| nothing like the Poisson or binomial distribution. Instead, it is highly skewed with  |
| degrees that extend to several orders of magnitude. The degree distribution of real  |
| networks can often be well modeled with a power law expression. Meaning that the  |
| probability that the node has degree k drops proportionately to k raised to a negative  |
| exponent alpha. For instance, the plots that you see here illustrate the measured degree  |
| distribution of an older Internet topology at the router level, a protein-protein  |
| interaction network. An email social network, which shows basically who sends email to  |
| whom. And a citation network showing which papers cite other papers. Note that the last  |
| two networks are directed and so the corresponding plots show separately, the in degree  |
| and the out degree distributions. You can find more information about these networks in  |
| table 41 of your textbook. This plot also shows in green, the Poisson distribution with  |
| the same average degree as the observed network. Please note the following points about  |
| these floats. The Poisson distribution is clearly a very bad model because it cannot  |
| capture the large variability and skewness of the degree distribution of these networks.  |
| Second, the plots are shown in log-log scale and the degree distributions decrease  |
| roughly as straight lines. This means that the probability that a node has degree k drops  |
| as a power k raised to a negative power. The slope of that straight line corresponds to  |
| the exponent of the power-law. This observation is not just a statistical technicality.  |
| The fact that real world networks often follow a power-law degree distribution has major  |
| implications about the function, robustness and efficiency as we will see later in the  |
| semester. |
