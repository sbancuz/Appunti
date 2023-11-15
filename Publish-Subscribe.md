---
tags:
  - distributed_systems
---

This type of communication has simple API with only 2 primitives:
- publish
- subscribe

Event notifications are simply messages. This type of architectures has 2 types of subscription methods:
- Subject-based -> Where the set of subjects is determined a priori, you can publish to a subject and all who are subscribed as well receive a notification
- Content-based -> The format of messages are key-value pairs and you only receive messages depending on their content

In these systems there is always an event dispatcher that receives all the messages and handles the dispatching. This is almost always a bottleneck in a system, but could be distributed into various message brokers.
### Acyclic

In an acyclic system these message brokers are implemented in 3 ways:
- Message forwarding -> a broker stores only his subscriptions and forwards the message to all the other brokers
- Subscription forwarding -> the subscription is know all over the network and the message always takes the shortest path
- Hierarchical forwarding -> assumes a rooted overlay tree, the subscription goes to the root broker and the message tries to forward the message toward the root util you find a subscription
### Cyclic
#### DHT Routing
In a cyclic one we use [[DHT]] based approach. To subscribe for messages you calculate the hashes, then we use the [[DHT]] to route to the node while leaving routing information to return messages back. To receive messages you calculate the hash, try to route using the [[DHT]] and when you find the route toward a subscriber you follow it. The problem with this approach is that it only works for subject based routing.
#### Content-based routing with PSF
To achieve content-based routing we put on every node a table that represents the SPT (shortest path tree) to every leaf node reachable, but it only stores the next hop. This tables keeps information stored in this structure:
- for each source $v$ the children in the SPT are associated with $v$
- for each children $u$, it holds a predicate that links all the predicates of all the reachable nodes $u$

The table created with this approach is fairly small, but it can be improved by introducing the concept of indistinguishable nodes. Two sources $A$ and $B$ with SPT $T(A)$ and $T(B)$ are indistinguishable from a node $n$ if $n$ has the same children for $T(A)$ and $T(B)$ and reaches the same nodes along those children.
#### Content-based routing with PFR
In the same way as the PSF we create only one SPT that link the subscriber to all other nodes reachable in the network. The source of the message calculates the set of receivers and it adds them to the header of the message, this means that every node knows only the subscriptions of all the reachable in the network. At every hop this set is partitioned in 
- Unicast table
- Forwarding table