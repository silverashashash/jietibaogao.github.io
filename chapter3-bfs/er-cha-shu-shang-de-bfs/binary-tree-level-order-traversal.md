##Binary tree level order traversal

http://www.lintcode.com/problem/binary-tree-level-order-traversal/



```py
#自己的答案
"""
Definition of TreeNode:
class TreeNode:
    def __init__(self, val):
        self.val = val
        self.left, self.right = None, None
"""
from collections import deque
class Solution:
    """
    @param root: A Tree
    @return: Level order a list of lists of integer
    """
    def levelOrder(self, root):
        # write your code here
        if not root:
            return []
        
        queue = deque()
        result = []
        
        queue.append(root)
        result.append([root.val])
        
        while len(queue):
            level = []
            for _ in range(len(queue)):
                head = queue.popleft()
                if head.left is not None:
                    queue.append(head.left)
                    level.append(head.left.val)
                if head.right is not None:
                    queue.append(head.right)
                    level.append(head.right.val)
            if level:
                result.append(level)
        
        return result

            


```

