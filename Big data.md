---
tags:
  - distributed_systems
---
Big data is a large portion of data science since it needs to handle a large volume of data to extract knowledge and insights from said data. This is a problem for distributed systems because such data needs to be transferred in large quantities and may come in all sorts of different formats.

>[!warning]
>This data may not always be correct

In many domain, information is relevant when it's fresh and loses its value with the passage of time. This means that this enormous amount of data needs to be processed quite rapidly.

So the objective becomes a system that is:
- Scalable
- Easy to change
- Has 
	- Automatic parallelization
	- [[Fault tolerance]]
	- Monitoring tools
	- Clean abstraction for programming

### Map reduce

In a map reduce problem the computation is divided in:
- Map in Key Value pair all the possible data
- Reduce all the values of a given key to only one

![[map reduce.png]]

>[!example]-
> Consider google maps. The map of the world can be represented as a [[Graphs]] in which all the nodes are points of interest and every edge is a directed road. We want to find the shortest path from lets say a point and the nearest gas station
> 
> ![[example map.png]]
> 
> The first thing that comes to mind is to use one of the widely known [[Search algorithm]] to find such path, but given their [[Complexity of an algorithm]] and the amount of data that is available this is not quite feasible. And even if it were, just sending this amount of data through some channel to perform the computation would be impossible.
> 
> To resolve this problem we need to make the right assumptions
> - All the data is not required, we can just take the portion that is relevant, say 50 km from every node is a block
> - All block are independent and can reside on any server
> 
> Now the computation is divided in:
> - Every block finds the distance of every node from the gas station
> - Re-assemble the data and using the intersections of the blocks, find the shortest path

To design a system able to compute such problems we need to resolve 3 problems:
#### Scheduling

We use a master-slave architecture in which:
- Data divided in M map tasks of 64 MB
- Reduce the results
- Automatic worker task management

A master node needs to also take into account the locality of the data
#### Distribution

The main objective is to minimize the network operations of the system. Files are divided in 64 MB with 3 copies each all saved on different machines, but still geographically near.
#### Fault tolerance

On worker failure the master will detect it through pings and assign new workers to re-execute the task. On master failure we can just re-elect a new one and resume the computation.
