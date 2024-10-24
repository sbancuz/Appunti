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

