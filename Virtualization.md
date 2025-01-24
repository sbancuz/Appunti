---
tags:
  - OS
---
A process virtual machine is designed to provide a programming environment that's independent of any specific platform. [[Virtual memory]] and [[CPU multiplexing#Task scheduling]] is a big part in their implementation. System level virtual machines provide an environment where multiple operating systems run under the assumption that a duplicate of the whole machine is dedicated solely to each operating system.

A **Virtual machine** is an efficient, isolated duplicate of the real system that can run a commodity OS. This definition relays on direct execution through what's called a **virtual machine monitor** or **Hypervisor**. To implement this we can highlight $3$ key requirements:
- Fidelity $\to$ equivalence with the original machine
- Safety $\to$ the virtual machine cannot override the host control of virtualized resources
- Efficiency $\to$ programs should show at most minimal slowdowns

Virtual machines allow us to consolidate and partition hardware. This means that rather than using a machine at $100\%$ for only one process, we can split $50\%$ for $2$. This allows for vertical scaling of servers since we can just make more virtual machine given enough computational power. Plus they also offer horizontal scalability when dealing with variable workload. As a last advantage they provide a secure, standardized infrastructure to deploy applications in complex environments.

There are $2$ types of hypervisors:
- Type $1$ $\to$ Native hypervisors or bare metal
- Type $2$ $\to$ Run inside another OS

To deal with the safety concern instructions are divided in $2$ types: **privileged** and **underprivileged** -- the former are those that trap in user mode. The idea is to run privileged instruction in a de-privileged mode. The problem is that we need to take into account the instruction sensitivity to virtualization before executing. We can define and instruction sensitive if it meets at least one criteria
- control sensitive $\to$  instruction modifies the machine state -- enable/disable interrupts
- behavior sensitive $\to$ instruction that act differently depending on whether they're used in user/super mode

>[!note] Popek and Goldberg theorem
>For any conventional computer, a virtual machine monitor may be built if the set of sensitive instructions for that computer is a subset of the set of privileged instructions.
### Software based virtualization

This type of virtualization is synonymous with **deprivileging** this means that a virtual machine functions with lesser access to hardware and system resources. To keep the abstraction intact we need ne hypervisor to intercept guest privileged instructions to emulate them. Deprivileging could still prove a problem in term of fidelity since a guest could understand that it's running in unprivileged mode. This is resolved, for software virtualization, through JIT compilation.  

![[virtual pages.png]]

The virtual machine will use **shadow pages**. This structure is used to avoid the translation from guest virtual address to guest physical address as this would imply in a major slowdown in the guest executions and would also give away the fact that a process is running in a VM. With shadow pages the hypervisor has to keep track of the page tables of the guest OS. Keeping track of pages has the advantage of knowing whether a page fault can be handled by the hypervisor or it needs to be forwarded to the host OS, thus speeding up fault resolution. 

There are other problems with pure **trap and emulate** systems. One is that it could happen that some platform could have unprivileged virtualization sensitive instructions, making it hard to keep track of the interrupts directly. Another problem is that of **excessive faulting**, on x86-32 `sysenter` and `sysexit` trap into the hypervisor any time a syscall is executed. Another problem is that there could be a lot of operational modes adding a lot of complexity.
### Hardware based virtualization

The goal here is to avoid any problem with deprivileging by adding a few new modes and allow the state of the guest to be saved in its entirety to be used in some shadow structures. It also would be nice to obey the Popek-Goldberg requirements and improve performance.

![[HW virtualization.png]]

Intel VT-x is Intel's answer to hardware virtualization on x86. One key feature of VT‐x is the creation of a dedicated root‐mode. This was achieved by duplicating the entire state of the processor to have full equivalence for virtualized workloads. **Root mode** is where Hypervisors and host operating systems operate from. The processor can switch mode in an atomic nature. This means that a single instruction or trap can initiate a transition from one mode to another. Root mode can be virtualized also $\to$ **recursive virtualization**

![[Extended page tables.png]]

Another addition of VT-x is **extended page tables**. This basically implemented shadow tables using hardware address translation with the downside of slowing down a bit the TLB miss.
### KVM

KVM is an open-source virtualization technology that turns the Linux kernel into a type-1 hypervisor. In this case VM run like threads. The idea is to reuse the scheduler, memory management and driver portfolio from the kernel to implement an hypervisor.

![[kvm.png]]

KVM also allows for **memory overcommitment**, this means that we can leverage Linux's virtual memory to allocate more VMs than we have memory. This is because most VMs don't use $100\%$ of their memory all the time. 

Another key concept is that of **ballooning**. We want to ensure that all virtual machines their physical memory usage below some maximum, so the idea is to associate to each VM physical memory a balloon that reserves a specific number of physical pages. Once we need more memory, for instance for another VM, we just inflate a balloon, thus forcing the OS to swap the to disk some machines and free up memory.

A technique used to save memory is **same-page merging** or **page deduplication**. The goal is to share memory pages that are identical between VMs. This works by having a process that checks for equivalence of memory pages and consolidates them if they are found identical. It's a bit heavy, but can be used also for normal processes.
#### QEMU

Even with KVM, implementing an fully-fledged hypervisor is not exactly easy. You still need to handle all the interaction with the hardware; so **emulated devices** and **hardware passthrough**. 