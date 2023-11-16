---
tags:
  - distributed_systems
---
In a hierarchical flat naming systems names are organized in a tree-like structure with every parent node that knows all the names of the leaf nodes. In this structure nodes are divided in domains in which the top node is called a **directory**. 

Name resolution in this scheme works by asking the closest directory node for the mapping, and if it doesn't know then it will ask it's directory node and so on. This works because the top level directory node will hold all the mappings for the system.