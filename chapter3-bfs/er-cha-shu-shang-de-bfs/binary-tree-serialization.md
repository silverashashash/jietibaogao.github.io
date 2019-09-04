## Binary Tree Serialization 
二叉树序列化
http://www.lintcode.com/en/help/binary-tree-representation/

题目及解答:
http://www.lintcode.com/en/problem/binary-tree-serialization/ http://www.jiuzhang.com/solutions/binary-tree-serialization/

####python的list和string如何转换
https://blog.csdn.net/roytao2/article/details/53433373


####这里只写了序列化的答案，没写反序列化的
```py
#自己的答案
#是否正确？
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
    @param root: An object of TreeNode, denote the root of the binary tree.
    This method will be invoked first, you should design your own algorithm 
    to serialize a binary tree which denote by a root node to a string which
    can be easily deserialized by your own "deserialize" method later.
    """
    def serialize(self, root):
        # write your code here
        if not root:
            return []
        
        queue = deque()
        result = [root.val]
        
        queue.append(root)
        
        while queue:
            for _ in range(len(queue)):
                head = queue.popleft()
                if head.left:
                    queue.append(head.left)
                    result.append(head.left.val)
                else:
                    result.append("#")
                if head.right:
                    queue.append(head.right)
                    result.append(head.left.val)
                else:
                    result.append("#")
                    
        return "".join(result)
```

