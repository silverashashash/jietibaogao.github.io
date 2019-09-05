## Converted Binary Tree to Linked Lists by Depth

[https://www.lintcode.com/problem/convert-binary-tree-to-linked-lists-by-depth/description](https://www.lintcode.com/problem/convert-binary-tree-to-linked-lists-by-depth/description)

#### Description

Given a binary tree, design an algorithm which creates a linked list of all the nodes at each depth \(e.g., if you have a tree with depth D, you'll have D linked lists\).

#### Example

Example 1:

```
Input: {1,2,3,4}
Output: [1->null,2->3->null,4->null]
Explanation: 
        1
       / \
      2   3
     /
    4
```

Example 2:

```
Input: {1,#,2,3}
Output: [1->null,2->null,3->null]
Explanation: 
    1
     \
      2
     /
    3
```

思路：

* 按层遍历
* 重点是如何建立一个linked list？

```py
#自己的答案
#看答案才知道要用dummyNode
#感觉就跟初始化一样
"""
Definition of TreeNode:
class TreeNode:
    def __init__(self, val):
        this.val = val
        this.left, this.right = None, None
Definition for singly-linked list.
class ListNode:
    def __init__(self, x):
        self.val = x
        self.next = None
"""
from collections import deque
class Solution:
    # @param {TreeNode} root the root of binary tree
    # @return {ListNode[]} a lists of linked list
    def binaryTreeToLists(self, root):
        # Write your code here
        if root is None:
            return []

        queue = deque()
        result = []

        queue.append(root)

        dummy = ListNode(0)

        while queue:
            node_list = dummy

            for _ in range(len(queue)):

                head = queue.popleft()
                node_list.next = ListNode(head.val) #new 出来一个ListNode，它的value属性是head.val
                node_list = node_list.next

                if head.left:
                    queue.append(head.left)
                if head.right:
                    queue.append(head.right)

            result.append(dummy.next)    

        return result
```



