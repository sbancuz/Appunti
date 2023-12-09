---
tags:
  - distributed_systems
  - parallel_computing
---
In high performance networks we need higher level primitives for asynchronous, transient communication. It's a network and parallelization API more higher level than [[Berkeley sockets]] built on top of a [[Distributed memory model]]. 

In reality MPI is just a standard that defines a set of instructions for libraries to implement. MPI it's commonly used with [[OpenMP]] to scale over [[threads]] and MPI to scale over computation nodes. 
### Communication

The communication takes place within a known group of processes and within each group is assigned a pair of **(groupID, processID)**  that represents the connection.

>[!warning]
>There is no support for [[Fault tolerance]] but error handling is slowly being implemented
### API

At the beginning, we need to initialize MPI and negotiate the thread usage, then, at the end, we need to finalize it. Almost all functions will return `MPI_SUCCESS` or an error code. 

In the initialization we need to define the thread usage level:
- `MPI_THREAD_SINGLE` -> Only the main thread
- `MPI_THREAD_FUNNELED` -> Multi-threaded, only one thread with MPI
- `MPI_THREAD_SERIALIZED` -> Multi-threaded, only one thread at a time can call MPI
- `MPI_THREAD_MULTIPLE` -> Just multi-threaded

>[!warning]
>This initialization is important since it will describe how communication is done using MPI, thus impacting performance a lot
#### Init

```c
int MPI_Init_thread(int *argc, char ***argv, int required, int *provided)
```

This function will consume MPI specific `argc` and `argv`, `required` is the thread level and `provided` is the actual thread level that we get.
#### Finalize

```c
int MPI_Finalize(void)
```

This has to be the last MPI function to call and it has to be called after all the MPI requests have already been processed.
#### Communicator

Groups of processes that share a communication context are represented by a variable with type `MPI_Comm`. The initialization function created two communicators:
- `MPI_COMM_WORLD` -> all MPI process
- `MPI_COMM_SELF` -> only current process

```c
int MPI_Comm_size(MPI_Comm comm, int *size) // size = number of processes
int MPI_Comm_rank(MPI_Comm comm, int *rank) // rank = id of the process [0, size)
```
#### Point-to-point communication

This is a set of functions to send/receive a message between two processes. These calls may be either blocking or non-blocking. 

A message in MPI is composed by:
- the rank
- the tag that describes the topic of the message
- the content

```c
int MPI_Send(const void *buf, // Content of the message
			 int count, // number of elements to send (!!Not bytes)
			 MPI_Datatype datatype, // type of data to send
			 int dest, int tag, MPI_Comm comm) 
			 
int MPI_Send_c(const void *buf, 
			   MPI_Count count, // This is the only difference and its just the type
			   MPI_Datatype datatype, 
			   int dest, int tag, MPI_Comm comm) // when supported
```

There are 4 ways to handle outgoing messages in MPI and **all** the functions follow this same convention:
- synchronous `MPI_Ssend`-> send is blocking until there is matching `recv`
- buffered `MPI_Bsend` -> bundle messages together 
- standard `MPI_send` -> implementation chooses
- ready  `MPI_Rsend` -> send can start iff matching `recv` is already started

To specify the `MPI_Datatype` there is an enum `POD` to *build* our datatype.

![[mpi datatype.png]]

```c
int MPI_Recv(void *buf, // Data
			 int count, // Number of elements
			 MPI_Datatype datatype, 
			 int source, // Use MPI_ANY_SOURCE if unknown 
			 int tag, MPI_Comm comm, 
			 MPI_Status *status) // Some message information
int MPI_Recv_c(void *buf, 
			   MPI_Count count, // Another count that is not int like before
			   MPI_Datatype datatype, 
			   int source, int tag, MPI_Comm comm, 
			   MPI_Status *status) // when supported
```

To get the message information we use:
```c
int MPI_Get_count(const MPI_Status *status, MPI_Datatype datatype, int *count)
int MPI_Get_count_c(const MPI_Status *status, MPI_Datatype datatype, MPI_Count *count)
```

However this is a bit of a chicken and egg problem if we don't know first the message size , to get the actual size to alloc for the read buffer we need to probe the message and dynamically allocate the receiving buffer.
```c
int MPI_Probe(int source, int tag, MPI_Comm comm, MPI_Status *status)
```

