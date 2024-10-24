---
tags:
  - OS
---
![[kernel mem.png]]

This is the Linux virtual address space. Each process uses a unique page directory with user‐mode mappings at the bottom and shared global kernel mappings at the top. **Kernel logical** addresses map directly to physical addresses starting from *zero*, simplifying kernel operations. 
This space includes the kernel itself, allowing easy referencing of physical addresses. To allocate contiguous memory in this area, you use the `kmalloc` function. Kernel virtual addresses, however, might not map to contiguous physical pages. For these mappings, `vmalloc` is used, handling non‐contiguous memory requests efficiently.

Though crucial for handling [[virtual memory]], page tables only account for pages currently in memory. This leaves out pages that aren’t currently loaded. To enable lazy loading of pages Linux uses VMAs -- Virtual Memory Areas. They define a range of virtual addresses utilized by a process. Additionally, VMAs facilitate **efficient data retrieval** for pages not currently mapped. They maintain
information about the corresponding data source, whether on disk or in existing memory pages. 

>[!note]
>VMAs can map to files, so whenever a page gets evicted there is a write back, or to nothing. These types of mapping are called **anonymous**, they got in the swap whenever they get evicted.

A **page fault** is produced by a mismatch of a load/store address and the properties of the page table entries. In the Linux kernel, efficient memory protection relies on translating Read, Write, and Execute access rights of VMAs in Page Table entries (ptes) access rights.In principle, flags could just be copied however the way in which ptes flags are constructed is more complex due to **demand paging** and **copy on write**.

Demand paging defers page frame allocation, reducing memory usage by allocating frames only upon access, addressing pages only as needed. Here, page faults trigger memory allocation for valid but non‐resident pages, with specific initialization based on page type and access history.

On the other hand copy on write is quite simple. Instead of duplicating page frames, they are shared between the parent and the child process. However, as long as they are shared, they cannot be modified. Whenever the parent or the child process attempts to write into
a shared page frame, an fault occurs and copies the page.