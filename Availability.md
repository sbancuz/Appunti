---
tags:
  - distributed_systems
---
Replicating machine makes the system more performant since it allows more throughput and can reduce latency for the requests. For example if we spread servers around the world, it's likely that someone in the USA will have the same experience of someone in the EU. These types of servers are called [[CDN]]s. 

The problems with replication is data [[Distributed consistency model|consistency]], what will happen is something changes in a replica?
To solve this issue we define a [[Distributed consistency model]].