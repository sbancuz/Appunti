---
tags:
  - parallel_computing
---
### Dictionary problem

Given an universe $(U, <)$ of keys with a total order and the goal is to maintain a set $S \subseteq U$ under the following operations:
- Search
- Insert
- Delete

Other operations may be defined based non the implementation: Min, Max, List, Union, Split

But how do we implement this?
1) Unordered Array
	1) Searching: $O(n)$
	2) Inserting/Deleting: $O(1)$
2) Ordered Array
	1) Searching: $O(\log n)$
	2) Inserting/Deleting: $O(n)$
3) BST
	1) Search/Insert/Deletion: $O(\log n)$ if balanced
	2) The expected depth for insertion is $1.39\log n$
4) AVL tree -> Self balancing tree, but hard to implement
	1) Search/Insert/Deletion: $O(\log n)$ 
5) Splay tree -> Self balancing tree
	1) Search/Insert/Deletion: $O(\log n)$ 
6) [[Random Treaps]] 
7) [[Skip list]]

>[!note]
>The idea behind the splay tree is to put in the root a node accessed by a FIND operation, and if it is accessed enough it will remain at the top of the tree
