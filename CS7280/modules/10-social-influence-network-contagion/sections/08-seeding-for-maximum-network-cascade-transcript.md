# Constrained Optimization Problem

| Text |
|------|
| An important problem in the context of network diffusion is, how to select a subset of k  |
| nodes, that if activated, can collectively create the largest network cascade. In the  |
| context of marketing for instance, an advertising company may want to promote a certain  |
| product through an online social network, such as Facebook. Suppose that they can give  |
| the product for free to k users. They expect that this k users will then influence their  |
| neighbors, online friends, to buy the same product and also influence their own friends,  |
| creating a network cascade. Obviously, the marketing company would like to select the set  |
| of k nodes, that can cause the maximum sites cascade. Mathematically this can be stated  |
| as a constrained optimization problem. We're given a weighted and potentially directed  |
| network, and a diffusion model such as the linear threshold or the independent cascade  |
| model. Let S be a set of nodes, that we initially activate, the sources in other words.  |
| F(S) represents the set of nodes that will eventually become active, including those in  |
| S. After [inaudible] the cascade, f(S) is referred to as the cascade size, that started  |
| from the sources S. The objective here is to select the set S, such that f(S) is maximum,  |
| subject to the constraint that the size of S is at most k nodes. When the network  |
| diffusion model is probabilistic, such as the independent cascade model, the objective is  |
| to maximize the expected value of f(S). The visualization here shows two cases, when k is  |
| equal to 2. In the first case, we initially activate nodes D and E, and the cascade does  |
| not extend beyond those two nodes. In the second case, we activate initially nodes A and  |
| E. Here, the cascade eventually, covers the whole network. |
