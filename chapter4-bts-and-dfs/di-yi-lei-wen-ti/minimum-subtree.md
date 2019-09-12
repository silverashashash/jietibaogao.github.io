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
import sys
class Solution:
    """
    @param root: the root of binary tree
    @return: the root of the minimum subtree
    """
    def findSubtree(self, root):
        # write your code here
        if not root:
            return None

        min_node, min_sum, total_sum = self.dfs(root)
        return min_node
        
    def dfs(self, root):
        if root is None:
            return root, sys.maxsize, sys.maxsize
        
        left_min_node, left_min_sum, left_total_sum = self.dfs(root.left)
        right_min_node, right_min_sum, right_total_sum = self.dfs(root.right)
        
        total_sum = root.val + left_total_sum + right_total_sum
        
        if left_min_sum < right_min_sum:
            min_sum = left_min_sum
            min_node = left_min_node
        else:
            min_sum = right_min_sum
            min_node = right_min_node
            
        
        if total_sum < min_sum:
            min_node = root
            min_sum = total_sum

        
        
        return min_node, min_sum, total_sum
                

         
```
- 答案是空，为啥？
    - 因为``sum_total`` return为``sys.maxsize``了，应该改成``0``，否则sum_total 咋跟 sum_min 比较啊？？？
* 


