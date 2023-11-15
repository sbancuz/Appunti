---
tags:
  - distributed_systems
---
In distributed computing, a **remote procedure call** (**RPC**) is when a computer program causes a procedure to execute on a shared network, which is written as if it were a normal (local) procedure call. That is, the programmer writes essentially the same code whether the subroutine is local to the executing program, or remote. This is a form of [[Client server]] interaction, typically implemented via a request–response message-passing system. In the object-oriented programming paradigm, RPCs are represented by remote method invocation (RMI). 

The RPC model implies a level of location transparency, namely that calling procedures are largely the same whether they are local or remote, but usually, they are not identical, so local calls can be distinguished from remote calls. Remote calls are usually orders of magnitude slower and less reliable than local calls, so distinguishing them is important.

Another important aspect is that the procedures' parameters are always passed by value. 

![[RPC.png]]
### IDL

The interface definition language raises the level of abstraction. Given the types and the interfaces, it generates the stub code that needs to perform the communication layer. This will also automatically generate serialization and marshalling code.
### Server resolution

To find out which server provides a given service you can either hard-code the server information of try to find it out through the network.

To resolve this problem it was developed **portmap**, a daemon decodes the packet and binds calls and server/ports.
There is also a directory machine that enables location transparency.

Leaving the servers always running is a bad idea since it would waste computing power and resources, so there exists another server that manages the processes in the entire system. It's a form of load balancing.
### Lightweight RPC

This is s lighter version of RPC that is implemented on top of the process inside a single machine. This way we can have a shared memory region that every process has access to. This greatly improves communication speed and reliability. This approach has a couple of advantages:
- less threads
- less memory
- less resource usage
### Asynchronous RPC

RPC preserves the usual call behavior, but the execution resumes after the server responds with the acknowledge and goes on. This is usually implemented with procedures that don't return anything but,  to deal with the results of the call, the callee may invoke the caller back. 
The implementation of RPC also batches the calls to optimize the procedures.
### RMI

Is the object-oriented version of RPC, in this remote object can be passed around, but the core concepts and mechanisms with RPC remains the same. The one key difference here is that the IDL can implement stubs to pass object by reference. Here IDL can handle inheritance, exception handling, etc...
