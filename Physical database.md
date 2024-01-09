---
tags:
  - databases
---
The data inside a database must be stored in 2 separate types of memory: **main** -- stored in pages -- and **secondary** -- stored in blocks.

>[!warning]
>For data to be utilized it must be transferred onto main memory

Primary memory is composed of RAM and secondary memory can be compromised of SSD and [[Hard Drive]] and data must be stored mainly into files onto secondary memory for 2 reasons:
- Size
- Persistence

The main difference between the two types of memory is the access time divided in
- **seek** time $\to$ search the data in physical memory
- **latency** time $\to$ time to wait before it can actually read
- **transfer** time $\to$ data transfer time
Primary memory is 4 orders of magnitude faster than secondary and for I/O bound applications, this matters a lot.

The [[DBMS]] depends on the file system only to manage secondary memory access and it directly manages the file organization. In some  cases it can even manage location of blocks in memory.
### Access methods

Software that provides data access and manipulation primitives for each data structure, and it organizes data:
- each table is stored in one **primary** physical data structure
- may have one or more many optional **secondary** access structure like indexes

Regardless of the data structure, they are created in 3 different methods
- [[Sequential access structure]]  $\to$ used only in primary
- [[Hash based access structure]] $\to$ more frequent in secondary, but still used for primary
- [[Tree based access structure]] $\to$ mainly used in secondary
### Blocks and tuples

To represent memory we use **blocks** and **tuples** that represent the physical and logical component respectively

![[tuples.png]]

In order to estimate the cost of a query we use the **block factor** $B$ with the tuple size $ST$ and size of a block $SB$
$$
B = \left \lfloor \frac{SB}{ST} \right\rfloor
$$
>[!warning]
>In our cost model we assume pages of equal size and organization as blocks