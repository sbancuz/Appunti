---
tags:
  - distributed_systems
---
In this schema the names are **flat** --represented as string without -- and it's resolution can be:
- simple solutions designed for small-scale environments like broadcast (ARP), multicast or forwarding pointers (for mobile devices)
- home-based approaches, in this solution a clients always contacts the 'home server' and it knows how to find the receiver (used for example for mobile IP and cellphone networks) 
- [[DHT]]
- [[Hierarchical flat naming]] approaches that generalize the search of a local registry in a tree-like structure in which the top nodes has all the information for the leaves