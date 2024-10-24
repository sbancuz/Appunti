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

But what actually happens on a page fault?

![[page fault.png]]

When a process tries to access an address that falls within a VMA but lacks a page table entry, the function `handle_mm_fault` is invoked to configure the missing entry. Once the PTE has been setup will fill the corresponding entry with a mapping to a physical page.

>[!note]
>Choosing which physical page, or even allocate a new one, depends on the operation and the type of VMA.
### Allocators

The base that every kernel allocator uses is the buddy allocator.

![[allocators.png]]

The buddy allocator has to manage memory in a NUMA context, so it must be aware of the actual architecture of the machine. This is obvious since allocating on another node is way more costly than allocating on a local one. So, to keep pages close to each other the kernel divides the memory into contiguous chunks called **zones**.

![[zones.png]]

There are other allocator in the kernel, but they may depend on the buddy allocator:
```c
void *kmalloc(size_t size, int flags);
```

This is the most common, and it's used as a general purpose allocator for small chunks of memory. Normally the operation can sleep unless `GFP_ATOMIC` is set, so one has to be careful to not call this is outside of process context. Use `GFP_KERNEL` for normal use or `GFP_USER` if it's a userspace mapping. It uses the slab allocator to access physical memory.

```c
void *get_zeroed_page(unsigned int flags);
void *get_free_pages(unsigned int flags, unsigned int order);
```

These are used to allocate large chunks of memory. This can be called at any time BUT they may fail due to the lack of memory. 

>[!warning]
>Over-allocation can quickly degrade system responsiveness

```c
struct page *alloc_pages_node(int nid, unsigned int flags, unsigned int order /* Size 2^order */);
```

This is for when you want to have precise control of where to allocate down to the NUMA level -- which node/CPU. 

```c
void *vmalloc(unsigned long size);
```

This allocates contiguous regions of memory in the virtual address space -- not necessarily contiguous in physical memory. It's important to not use this function for small allocation due to it's big overhead. Also it's not safe to call it in an atomic context.

---
In general within the kernel allocation and deallocation of fixed sized structures is very common. So we want an allocator that can handle these structures and that does not cause fragmentation. So we define $2$ different allocators:
- Quicklist $\to$ Only used for paging
- Slab allocator $\to$ Used for everything else

![[slab allocator.png]]

The slab allocator is a set of APIs used to create caches within the kernel on specific objects. These caches are called `kmem_cache` and there is one for each data structure managed by the kernel.

>[!warning]
>Allocations with slab allocators do not use locks

Freeing an object keeps it initialized, facilitating faster reuse. This strategy optimizes memory allocation, providing rapid access and minimizing overhead. There are $2$ types of caches:
- **dedicated** $\to$ for common structs like the `task_struct`
- **generic** $\to$ divided in areas with size of powers of $2$
