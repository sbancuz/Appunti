---
tags:
  - distributed_systems
---

This type of communication has simple API with only 2 primitives:
- public
- subscribe

Event notifications are simply messages. This type of architectures has 2 types of subscription methods:
- Subject-based -> Where the set of subjects is determined a priori, you can publish to a subject and all who are subscribed as well receive a notification
- Content-based -> The format of messages are key-value pairs and you only receive messages depending on their content

In these systems there is always an event dispatcher that receives all the messages and handles the dispatching. This is almost always a bottleneck in a system, but could be distributed into various message brokers.

In an acyclic system these message brokers are implemented in 3 ways:
- Message forwarding -> a broker stores only his subscriptions and forwards the message to all the other brokers
- Subscription forwarding -> the subscription is know all over the network and the message always takes the shortest path
- Hierarchical forwarding -> assumes a rooted overlay tree, the subscription goes to the root broker and the message tries to forward the message toward the root util you find a subscription

In a cyclic one we use [[DHT]] based approach. To subscribe for messages you calculate the hashes, use the [[DHT]] to route to the node while leaving routing information to return messages back. To receive messages you calculate the hash, try to route using the [[DHT]] and when you find the route toward a subscriber you follow it.