---
tags:
  - distributed_systems
---
In distributed computing, a **remote procedure call** (**RPC**) is when a computer program causes a procedure to execute on a shared network, which is written as if it were a normal (local) procedure call. That is, the programmer writes essentially the same code whether the subroutine is local to the executing program, or remote. This is a form of [[Client server]] interaction, typically implemented via a request–response message-passing system. In the object-oriented programming paradigm, RPCs are represented by remote method invocation (RMI). 

The RPC model implies a level of location transparency, namely that calling procedures are largely the same whether they are local or remote, but usually, they are not identical, so local calls can be distinguished from remote calls. Remote calls are usually orders of magnitude slower and less reliable than local calls, so distinguishing them is important.