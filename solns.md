---
layout: page
title: "HW6 Solns: CMPT231"
subtitle: "Lecture 6, ch13,18"
ext-js: "https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=AM_CHTML"
---

### HW6 Solutions (20pts)

+ (1a) *(3pts)* Show the tree:

  By level: S / HL + V / D + K + MQ + T + XZ

+ (1b) *(1pt)* How many splits?

  5

+ (1c) *(1pt)* Show the tree after deleting `M`.

  By level: S / HL + V / D + K + Q + T + XZ

  (This was a typo; I intended the question to delete H,
  which would have been more interesting.)

+ (2) *(2pts)* Max number of keys:

  Root node has \`2t-1\` keys and \`2t\` children. <br/>
  Level 1 has a total of \`2t(2t-1)\` keys, and \`(2t)^2\` children. <br/>
  Level 2 has a total of \`(2t)^2(2t-1)\` keys, and \`(2t)^3\` children. Etc.<br/>

  Summing Level 0 and Level 1:
  \`(2t)-1 + (2t)(2t-1) = -1 + (2t)(2t) = (2t)^2 -1\` <br/>
  Add in Level 2: \`(2t)^2-1 + (2t)^2(2t-1) = -1 + (2t)^2(2t) = (2t)^3-1\`

  We see that for *h* levels (including root),
  the max number of keys is \`(2t)^h-1\`.

+ (3a) *(1pt)* Largest value of *t*:

  20 \* (2t-1) keys + 8 \* (2t) pointers &le; 4096 <br/>
  So t = floor(147/2) = 73.

  (In the [real BTRFS](http://www.coderplay.org/btrfsdev/BTRFS-BTree-Structure.html), the header is 44 bytes, so the Knuth order is 144, corresponding to t=72.)

+ (3b) *(2pts)* How many keys:

  Use question (2) and t=73 and h=8:
  \`(2\*73)^8-1 ~~ 2.0645\*10^17\`, or over 206 quadrillion.
  <br/>(For instance, this is the upper limit on total number of files
  that can be stored in a single BTRFS volume.)

+ (3c) *(1pt)* How many key comparisons:

  Assuming linear search as described in lecture, the max number of
  comparisons happens when searching for the largest key in the tree.
  At each level, we need to compare against 2t-1 keys.
  So we need a total of h(2t-1) = 8(145) = 1160 key comparisons.

  The root node is always kept in memory, but we need to fetch 7 other nodes.

+ (4) *(9pts)*  (B-tree programming project)
