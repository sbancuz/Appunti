---
tags:
  - parallel_computing
---
This pattern is used to divide the work into specific domains and then reassemble the result. It generalizes the [[Geometric decomposition]] and allows to parallelize fork join and divide and conquer approaches.

With this data is divided in equally sized non overlapping regions of data in order to avoid conflicts.