# Other Network Tomography Problems

| Text |
|------|
| There are several other interesting problems in the network tomography literature. Here  |
| we simply mention a couple of them. In a computer network, links can be in a congested  |
| state, causing performance problems, such as queuing delays or packet losses in every  |
| end-to-end path that goes through those links. Suppose that we have a number of sensors  |
| and we can monitor the performance of several end-to-end paths shown here in red between  |
| those sensors. If none of the links is congested, then all of the paths will appear as  |
| not congested. If however, one link becomes congested, then the paths that go through  |
| that link will also appear in the path measurements as congested. In this visualization,  |
| the two orange paths are congested and they may be introducing large queuing delays and  |
| packet losses. Which link do you think is the cause of these problems? If we assume that  |
| there is only one congested link and congestion can only take place between routers, not  |
| between sensors and routers, then the most parsimonious explanation in this scenario  |
| here, is that the link that is shared by both congested paths, shown here in red, is also  |
| congested. In general, as long as we know the topology of the network and they're out  |
| between every pair of sensor nodes, we can usually identify the link or sequence of links  |
| that may be congested. In the context of communication networks, each link is associated  |
| with the propagation delay. Suppose that we want to estimate these link delays given  |
| end-to-end delay measurements. The delay of a path is equal to the sum of the link delays  |
| in that path. For instance, in this small network we see here we have three links with  |
| unknown delays. Suppose that we measure using a software tool such as Pink, that the  |
| delay in the path between A and B is 30 milliseconds, between A and C is 40 milliseconds,  |
| and between B and C is 50 milliseconds. Further, suppose that we know the topology of the  |
| network and the route or sequence of links in its path. We can express this problem as a  |
| system of linear equations in which the unknowns are the link delays and each equation  |
| corresponds to a distinct path. In this case, the linear system has a unique solution for  |
| the delay of each link shown here in the visualization. In practice however, such systems  |
| are often under constraint because the number of unknowns, the number of links, is more  |
| than the number of equations or paths. In such cases, we need to make additional  |
| assumptions about the links in order to be able to solve the linear system. Another  |
| interesting tomography problem in the context of transportation or communication networks  |
| is to estimate the amount of flow or traffic between every pair of end-points. This is  |
| also known as the traffic matrix inference problem. For instance, in this visualization  |
| we have four antinodes, the cities Atlanta, Boston, Chicago, and Detroit. The directed  |
| flows between these four cities may refer to the number of trucks driving between the  |
| cities every day. Suppose that we know the underlying road network and the route that is  |
| followed between every pair of cities. Further, suppose that we know for each of these  |
| links, the traffic volume on that link, it could be the number of trucks per day on that  |
| highway segment. How would you use such link level traffic volumes to estimate the  |
| unknown path level directed flows? Try to write down a system of linear equations for  |
| this network, so that each of the directed flows between two cities corresponds to an  |
| unknown and its network link gives us an equation. As you will see in many cases, we have  |
| more unknowns than equations, meaning that again we're dealing with an underspecified  |
| problem. As we just saw the traffic matrix inference problem is often under-constrained  |
| because the number of unknowns is typically larger than the number of equations. One way  |
| to add some more structure into the problem is to consider a model that describes the  |
| traffic flow between two-end nodes based on certain properties of those nodes, such as  |
| the population or the distance between them. A common sets model is the traffic gravity  |
| model. This model assumes that the traffic between two cities is proportional to the  |
| product of the populations PI and PJ of the two cities, and inversely proportional to the  |
| distance between the two cities, shown here as DIJ. The proportionality coefficient K is  |
| a variable that we can estimate based on the link level traffic volume measurements.  |
| Additional constraints are typically sufficient to solve the traffic matrix estimation  |
| problems we have in practice. |
