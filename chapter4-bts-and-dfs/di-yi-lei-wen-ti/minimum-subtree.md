## Minimum Subtree

[https://www.lintcode.com/problem/minimum-subtree/](https://www.lintcode.com/problem/minimum-subtree/)

[https://leetcode.com/problems/sum-of-subarray-minimums/](https://leetcode.com/problems/sum-of-subarray-minimums/)

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
            return root, None

        left_node, left_min = self.dfs(root.left)
        right_node, right_min = self.dfs(root.right)

        if left_node.val > root.val:
            minNode, minValue = root, root.val
        else:
            minNode, minValue = left_node, left_node.val

        if right_node.val < minValue:
            minNode, minValue = right_node, right_node.val

        return minNode, minValue
```

* 又是一个type混乱的题
* 


