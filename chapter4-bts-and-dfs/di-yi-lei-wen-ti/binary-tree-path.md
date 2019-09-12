## Binary Tree Path

[https://www.lintcode.com/problem/binary-tree-paths](https://www.lintcode.com/problem/binary-tree-paths)



- traveral
    - ``pop()``做回溯
    - number of islands 这题用dfs没有回溯，因为找的是所有的点（有去有回找的是路程，有去无回找的是点）
    - ``results[]``作为参数传递，好于用全局变量
    
- divide and conquer 
    - 整棵树的路径和左右子树的路径的关系？
    - 注意root是叶子结点的时候需要特殊处理（``root.right`` 和root.left都是None）
    
    
- return a list of string 这个怎么实现？
    
    
    


```py
# 看了答案的
"""
Definition of TreeNode:
class TreeNode:
    def __init__(self, val):
        self.val = val
        self.left, self.right = None, None
"""

class Solution:
    """
    @param root: the root of the binary tree
    @return: all root-to-leaf paths
    """
    def binaryTreePaths(self, root):
        # write your code here
        if root is None:
            return []
        
        paths = self.dfs(root)

        return paths 
        
    def dfs(self, root):

        if root is None:
            return []
            
        if root.left is None and root.right is None:
            return [str(root.val)]
        
        paths = []
        
        left_path = self.dfs(root.left)
        right_path = self.dfs(root.right)
        

        for path in left_path:
            paths.append(str(root.val) + '->' + path)
        for path in right_path:
            paths.append(str(root.val) + '->' + path)
        
        return paths
```
- 搞清楚左右子树和root的关系很重要
- root为叶子结点的判断不能少

