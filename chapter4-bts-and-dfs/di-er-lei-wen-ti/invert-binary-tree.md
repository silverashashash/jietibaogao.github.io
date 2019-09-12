## Invert Binary Tree
https://www.lintcode.com/problem/invert-binary-tree/
https://leetcode.com/problems/invert-binary-tree/

- 这题跟上题很像，是否也需要一个helper函数？



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
    @param root: a TreeNode, the root of the binary tree
    @return: nothing
    """
    def invertBinaryTree(self, root):
        # write your code here
        self.helper(root)
        
    def helper(self, root):
        if root is None:
            return None
        
        left_cur = self.helper(root.left)
        right_cur = self.helper(root.right)
        
        root.left = right_cur
        root.right = left_cur
        
        return root
        

```

问题
- 一开始直接``left_cur, right_cur = right_cur, left_cur``出错