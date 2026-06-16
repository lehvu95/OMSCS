# Example Network Communities: Zachary's Karate Club

| Text |
|------|
| In some instances of the community detection problem, we're fortunate to know the correct  |
| communities based on additional information about that data set. In other words, we know  |
| the ground truth. A famous such case is Zachary's Karate Club network. Zachary was a  |
| sociologist that started the interactions between 34 members of a karate club in the  |
| early 1970s. He documented the pairwise interactions between all members of the club. And  |
| he found 78 such edges, pairs of members that interacted regularly outside the club. What  |
| made the data set famous is that the president of the club and the instructor had a  |
| conflict at some point. And so the club split into two groups. About half of the members  |
| followed the instructor into a different club. So we do know for this data set that there  |
| were actually two communities. And we know that exact membership of its community. These  |
| two communities are shown in the visualization with circles versus squares. Today, any  |
| proposed community detection algorithm is also evaluated with the Zachary Karate Club  |
| data set. It is a very small data set, but it is one of the very few cases in which we  |
| know the ground truth. The four different colors in the visualization show the results of  |
| a community detection algorithm that we will discuss later in this lesson referred to as  |
| modularity maximization. Note that the algorithms detects four communities instead of  |
| two, which is the right answer. It manages to correctly identify two communities, the  |
| green and the orange that represent the club members that follow the instructor to a  |
| different lab. And two other communities, the white and the purple that represent members  |
| that stayed with the club president. |
