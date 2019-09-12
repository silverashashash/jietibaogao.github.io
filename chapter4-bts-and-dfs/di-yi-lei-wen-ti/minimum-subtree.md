## Minimum Subtree

[https://www.lintcode.com/problem/minimum-subtree/](https://www.lintcode.com/problem/minimum-subtree/)

```py
"""
Definition of TreeNode:
class TreeNode:
    def __init__(self, val):
        self.val = val
        self.left, self.right = None, None
"""

class Solution:
    """
    @param root: the root of binary tree
    @return: the root of the minimum subtree
    """
    def findSubtree(self, root):
        # write your code here
        if not root:
            return None

        node, min_val = self.dfs(root)
        return node

    def dfs(self, root):
        if root is None:
             return 0
         
         left_minNode, left_minSum = self.dfs(root.left)
         right_minNode, right_minSum = self.dfs(root.right)
         
         total = left_
         
         return left_Sum + right_Sum + root.val
         
```

* 又是个混乱的题目
* 


