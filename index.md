---
layout: page
title: "HW6: CMPT231"
subtitle: "Lecture 6, ch13,18"
ext-js: "https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=AM_CHTML"
---

{% include policies.md %}
{% include programming.md %}

### HW6 (20pts) [(solutions)](solns)

1. Consider an empty **B-tree** of *t=2*.
  + (a) *(3pts)* Demonstrate **insertion** of the following character keys
    in order: <br/> `D H T L S M V X K Z Q`
  + (b) *(1pt)* How many **splits** were needed in part (a)?
  + (c) *(1pt)* Show the tree after **deleting** `M`.
2. *(2pts)* Derive the **maximum** number of keys that can be stored in a B-tree (including internal nodes, not a B+-tree), in terms of *t* and the height *h*.  Show your work.
3. In the Linux **BTRFS** filesystem (default configuration), each node is 4KB = 4096 bytes (the **block size**). Each **key** takes 20 bytes, and each **pointer** to a child node is 8 bytes.
  + (a) *(1pt)* What is the largest value of *t* for a **B-tree** with such nodes? (In reality, the *header* also takes up some space, but you can ignore that.)
  + (b) *(1pt)* A 3-bit field tracks the **height** of each node, which means the B-tree can have at most 8 levels. Approximately how many **keys** can be stored in such a B-tree?
  + (c) *(1pt)* Compute the maximum number of **key comparisons** that need to be done in order to find a key in such a B-tree. How many **disk accesses** (fetching nodes/blocks from disk)?
3. **Programming Project**: Implement a B-tree for integer keys. Use pre-emptive split/merge as described in lecture.  You may limit yourself to *t* &le; 10 if it makes things easier. The policies stated above for programming assignments apply.  Your code should have:
  + (a) *(2pts)*  **Class** definitions and **constructors** for a single node and for the tree as a whole. *t* should be a parameter the user can set when instantiating the tree.
  + (b) *(3pts)* `insert( key )`: the return value should be the number of **disk accesses** needed (excluding the root node). If the key already exists, don't modify the tree.
  + (c) *(1pt)* `size()`: return the number of keys currently stored in the tree.
  + (d) *(3pts)* **Pre-order** and **in-order** tree traversals to print out the tree. (In-order traversal should print the keys in order.) You may use these to verify insertion works correctly.
  + (e) *(2pts)* **Extra credit** (optional): `delete( key )`, returning the number of disk accesses. Handle non-existent key gracefully.
