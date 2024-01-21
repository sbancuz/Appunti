---
tags:
  - distributed_systems
---
We assign timestamps to each transaction with a [[Global clock]], write operation on a data item $x$ are recorded in tentative versions, each with its own write timestamp $ts(x)$ until commit is performed. Each data item also holds a read $ts(x)$.

The scheduler operates as follow:
1) When receives $write(T,x)$ at $ts$
	- If $ts>ts_{rd}(x)$ and $ts>ts_{wr}(x)$ perform tentative write $x_{i}$ with timestamp $ts_{wr}(x_{i})$ 
	- else abort $T$ since the write request arrived too late
2) Scheduler receives $read(T,x)$ at $ts$
	- If $ts >ts_{wr}(x)$ 
		- Let $x_{sel}$ be the latest version of $x$ with the write timestamp lower than $ts$
		- If $x_{sel}$ is committed perform read on $x_{sel}$ and set $ts_{rd}(x)=\max (ts,ts_{rd}(x))$
		- else wait until the transaction that wrote version $x_{sel}$ commits or abort then reapply 
	- Else abort $T$ since the read request arrived too late

This method is deadlock free and aborted transactions will reapply for a new timestamp and simply retry.