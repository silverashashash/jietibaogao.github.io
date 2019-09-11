## Validate Binary Search Tree

已经完全糊涂了 什么时候是node，什么时候是node.val

```py
# 参考九章的答案
"""
Definition of TreeNode:
class TreeNode:
    def __init__(self, val):
        self.val = val
        self.left, self.right = None, None
"""

class Solution:
    """
    @param root: The root of binary tree.
    @return: True if the binary tree is BST, or false
    """
    def isValidBST(self, root):
        # write your code here
        if root is None:
            return True
        
        isValid, max_value, min_value = self.dfs(root)
        
        return isValid
        
    def dfs(self, root):
        if root is None:
            return True, None, None
            
        left_isValid, left_maxValue, left_minValue = self.dfs(root.left)
        right_isValid, right_maxValue, right_minValue = self.dfs(root.right)
        
        if left_isValid is False or right_isValid is False:
            return False, None, None 
        if left_maxValue is not None and left_maxValue >= root.val:
            return False, None, None 
        if right_minValue is not None and right_minValue <= root.val:
            return False, None, None
        
        maxValue = right_maxValue if right_maxValue is not None else root.val
        minValue = left_minValue if left_minValue is not None else root.val
        
        return True, maxValue, minValue
        
```

* 其实这个node里存的要么是一个数字，要么是None
* 学习下这种表达：
 ```py
 minNode = leftMin if leftMin is not None else root.val
 maxNode = rightMax if rightMax is not None else root.val
 ```
* 注意在最后 获得最大最小值的时候别搞反了
```py
maxValue = right_maxValue if right_maxValue is not None else root.val
minValue = left_minValue if left_minValue is not None else root.val
```

