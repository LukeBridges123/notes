## Counting Rooted Binary Trees
Consider first the case of rooted, unlabled binary trees where "left" and "right" branches are considered distinct (these are called "planar" binary trees). So e.g. the following trees are considered distinct:
  o
 / 
o 
 \
   o
   
  o
   /
  o
 /
o
since the first one bends right at the bottom, while the second bends left. Such a tree on n vertices consists of the root node, with two successors which are themselves rooted planar binary trees (these may be "empty") trees. There are n-1 vertices total among the "child" trees; there could be an empty tree on the left and an (n-1)-vertex tree on the right, a 1-vertex tree on the left and an (n-2)-vertex tree on the right, and so on. So, letting $b_n$ be the number of rooted, unlabeled planar binary trees, we have $b_n = \sum_{i = 0}^{n-1} b_ib_{n - 1 - i}$, and this plus the initial conditions $b_0 = b_1 = 1$ are enough to guarantee that these trees are simply counted by the [[Catalan Numbers]]. 

