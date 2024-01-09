---
tags:
  - databases
---
The idea is to store data with a [[Hash table]] where the key are the key fields. They are very effective for random access operation, static sized table and point queries -- with equality predicate. 

The hashing works in 2 steps:
- **folding** $\to$ transforms the key values so that they become positive integers
- **hashing** $\to$ transforms the positive number into the number of the bucket 

