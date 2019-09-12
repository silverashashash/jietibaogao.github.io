## LCA II

[https://www.lintcode.com/problem/lowest-common-ancestor-ii/](https://www.lintcode.com/problem/lowest-common-ancestor-ii/)

### Description

Given the root and two nodes in a Binary Tree. Find the lowest common ancestor(LCA) of the two nodes.

The lowest common ancestor is the node with largest depth which is the ancestor of both nodes.

The node has an extra attribute `parent` which point to the father of itself. The root's parent is null.


```py
#root 多了一个parent 指针
"""
Definition of ParentTreeNode:
class ParentTreeNode:
    def __init__(self, val):
        self.val = val
        self.parent, self.left, self.right = None, None, None
"""

```

