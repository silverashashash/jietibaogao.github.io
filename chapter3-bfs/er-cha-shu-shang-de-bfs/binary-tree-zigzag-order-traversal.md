## Binary Tree Zigzag Order Traversal 
####Description
Given a binary tree, return the _zigzag_ level order traversal of its nodes' values. (ie, from left to right, then right to left for the next level and alternate between).
https://www.lintcode.com/problem/binary-tree-zigzag-level-order-traversal/description



思路：
- 用一个level_number记录层数是奇数还是偶数？



```py
#自己的答案
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None
from collections import deque

class Solution:
    def zigzagLevelOrder(self, root: TreeNode) -> List[List[int]]:
        if root is None:
            return []
        
        queue = deque()
        result = []
        level_number = 1
        
        queue.append(root)
        
        while queue:
            level = []
            for _ in range(len(queue)):
                head = queue.popleft()
                if level_number % 2 == 0:
                    level.insert(0, head.val)
                else:
                    level.append(head.val)
                if head.left:
                    queue.append(head.left)
                if head.right:
                    queue.append(head.right)

            level_number += 1
            result.append(level)
        
        return result
                    
                    
```
- Runtime: 48 ms, faster than 9.51% of Python3 online submissions for Binary Tree Zigzag Level Order Traversal.
- Memory Usage: 13.9 MB, less than 5.41% of Python3 online submissions for Binary Tree Zigzag Level Order Traversal.




```py
#九章答案
#层序遍历完之后，看层数，偶数层reverse一下即可。

from lintcode import TreeNode
"""
Definition of TreeNode:
class TreeNode:
    def __init__(self, val):
        this.val = val
        this.left, this.right = None, None
"""


class Solution:
    """
    @param root: The root of binary tree.
    @return: A list of list of integer include 
             the zig zag level order traversal of its nodes' values
    """
    def preorder(self, root, level, res):
        if root:
            if len(res) < level+1: res.append([])
            if level % 2 == 0: 
                res[level].append(root.val)
            else: 
                res[level].insert(0, root.val)
            self.preorder(root.left, level+1, res)
            self.preorder(root.right, level+1, res)
    def zigzagLevelOrder(self, root):
        self.results = []
        self.preorder(root, 0, self.results)
        return self.results

```




