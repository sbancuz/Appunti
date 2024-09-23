---
tags:
  - OS
---
To create this layer of isolation between processes, the OS creates for each process a **virtual memory space** using physical address translation. This has also the bonus of giving the illusion of having a lot more available memory then what it's actually available. Of course since we want to ensure that no process can affect any other just virtual addresses are not enough, theoretically another process can still write in the same physical memory, so to resolve this OS have **data access rights**, this includes also **mutual exclusion** to shared resources.

In order for [[Process]] to use virtual memory, they are assigned **virtual address spaces** that include all the memory locations that a program can reference. Typically they area isolated from others, but some regions can be shared. 

![[VAS.png]]

The VAS is built from various virtual memory areas, some derived from the program on-disk representation, some created dynamically, and others reserved for kernel space. Importantly the VSDO in Linux contains certain system calls that don't require high privilege, so when calling them the process doesn't need to enter kernel space.  

