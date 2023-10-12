---
tags:
  - distributed_systems
---
The distributed components encapsulate a data structure providing an API to access and modify it. The components interact through [[RPC]] using [[Peer to peer]], but most often it's implemented as a [[Client server]].

It's main advantage is to hide the complexity in accessing/managing shared data.