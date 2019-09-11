## Balanced Binary Tree

- 这题不能在主函数里直接用dfs，因为需要两个return value，所以可以写一个有两个return value的validate函数，再在这个函数里做dfs。



```py
# 自己的答案
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def isBalanced(self, root: TreeNode) -> bool:
        if root is None:
            return True
        
        is_balanced, length = self.dfs(root)
        return is_balanced
    
    def dfs(self, root: TreeNode):
        if root is None:
            return True, 0
        
        left_valid, left_len = self.dfs(root.left)
        right_valid, right_len = self.dfs(root.right)
        
        return left_valid and right_valid and abs(left_len - right_len) <= 1, max(left_len, right_len) + 1 

```
- 错误的点：
    - 一开始return里没有加上左右子树是否balanced的判断，导致一下testcase出错：
    ```
                1
              /  \
             2    3
            /      \
           4        7
    ```



