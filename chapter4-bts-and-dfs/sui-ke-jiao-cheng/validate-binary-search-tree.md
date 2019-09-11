 ## Validate Binary Search Tree
 
已经完全糊涂了 什么时候是node，什么时候是node.val



```py
# 参考九章的答案
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def isValidBST(self, root: TreeNode) -> bool:
        if root is None:
            return True
        
        is_valid, max_node, min_node = self.dfs(root)
        
        return is_valid
    
    
    def dfs(self, root):
        if root is None:
            return True, None, None
        
        left_isValid, left_maxNode, left_minNode = self.dfs(root.left)
        right_isValid, right_maxNode, right_minNode = self.dfs(root.right)
        
        if left_isValid is False or right_isValid is False:
            return False, None, None
        if left_maxNode is not None and left_maxNode >= root.val:
            return False, None, None
        if right_minNode is not None and right_minNode <= root.val:
            return False, None, None
        

        min_node = left_minNode if left_minNode is not None else root.val
        max_node = right_maxNode if right_maxNode is not None else root.val
        
        return True, max_node, min_node
    
        
```

