

``## LCA II

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
A, B 两个点向上走，分别记录路径，这题不用复杂的方法




```py
# 看了答案的结果
# 据说trail用set()会更快
class Solution:
    
    def lowestCommonAncestorII(self, root, A, B):
        
        trail = [root]
        
        while A is not root:
            if A is B:
                return A
            trail.append(A)
            A = A.parent 
        
        while B not in trail and B is not root:
            B = B.parent
    
        return B
```



