---
tags:
  - distributed_systems
aliases:
  - P2P
---
In peer to peer all components play the same role,  so there is no client and no server. This approach resolves some problems of [[Client server]] architecture because it allows the system to scale and removes the single point of failure that was the centralized server. It is an architecture that promotes the sharing of resources and services through direct exchange between peers.

In reality purely peer to peer are rare, usually there is a server that gives 'direction' to other peers on the network.
### Centralized source

To retrieve some document on a network i contact the central server, and it points me to the node that has that document. At the moment a node is connected to a centralized server it gives the list of all the documents that he is willing to offer.
### Query flooding

This is a fully decentralized network. The new node connects to a well known **anchor** node, then sends a ping message to discover other nodes. Pong messages are sent in reply from hosts offering new connections with the new node. This nodes willing to offer connections are called **super peer**.