## Binary tree level order traversal

[http://www.lintcode.com/problem/binary-tree-level-order-traversal/](http://www.lintcode.com/problem/binary-tree-level-order-traversal/)

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
- 我的做法是在for这一层的时候，把当前节点非空的左右儿子加到queue里，同时把左右儿子值也加到level里。但是这样就有可能把空串加进去。因为for之前把level初始化为空串了。所以append到result的时候要加个判断
- 九章的做法是在for这一层的时候，只加当前节点的值，再把左右非空儿子加到queue里。

```py
#九章答案
#用一个队列
from collections import deque

"""
Definition of TreeNode:
class TreeNode:
    def __init__(self, val):
        self.val = val
        self.left, self.right = None, None
"""

class Solution:
    """
    @param root: A Tree
    @return: Level order a list of lists of integer
    """
    def levelOrder(self, root):
        if root is None:
            return []

        queue = deque([root])
        result = []
        while queue:
            level = []
            for _ in range(len(queue)):
                node = queue.popleft()
                level.append(node.val)
                if node.left:
                    queue.append(node.left)
                if node.right:
                    queue.append(node.right)
            result.append(level)
        return result
```



