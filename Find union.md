---
tags:
  - operations_research
  - coding
---
This data structure represents a colored [[Graphs]] and allows to easily check for cycles. All nodes in a subgraph must have an associated color, and inside a graph only one color is allowed. When merging 2 subgraph we check if the colors are the same then we a loop. but if not we can safely merge the 2 graphs.