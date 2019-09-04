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


```py
#九章的答案（看评论有错？）
#同学上传的也可以看
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
    @param root: An object of TreeNode, denote the root of the binary tree.
    This method will be invoked first, you should design your own algorithm 
    to serialize a binary tree which denote by a root node to a string which
    can be easily deserialized by your own "deserialize" method later.
    """
    def serialize(self, root):
        if root is None:
            return ""
            
        # use bfs to serialize the tree
        queue = deque([root])
        bfs_order = []
        while queue:
            node = queue.popleft()
            bfs_order.append(str(node.val) if node else '#')
            if node:
                queue.append(node.left)
                queue.append(node.right)
            
        return ' '.join(bfs_order)

    """
    @param data: A string serialized by your serialize method.
    This method will be invoked second, the argument data is what exactly
    you serialized at method "serialize", that means the data is not given by
    system, it's given by your own serialize method. So the format of data is
    designed by yourself, and deserialize it here as you serialize it in 
    "serialize" method.
    """
    def deserialize(self, data):
        # None or ""
        if not data:
            return None

        bfs_order = [
            TreeNode(int(val)) if val != '#' else None
            for val in data.split()
        ]
        root = bfs_order[0]
        fast_index = 1
        
        nodes, slow_index = [root], 0
        while slow_index < len(nodes):
            node = nodes[slow_index]
            slow_index += 1
            node.left = bfs_order[fast_index]
            node.right = bfs_order[fast_index + 1]
            fast_index += 2
            
            if node.left:
                nodes.append(node.left)
            if node.right:
                nodes.append(node.right)
        
        return root

```



