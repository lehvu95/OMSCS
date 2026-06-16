# Application of the Friendship Paradox

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
