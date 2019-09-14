## Kth Smallest Element in BST
https://www.lintcode.com/problem/kth-smallest-element-in-a-bst/
https://leetcode.com/problems/kth-smallest-element-in-a-bst/

- 本题需要背下来
- 考点1: BST的in-order性质 （中序遍历的第k个）
- 考点2: BST的traversal非递归版本(iteration)
    - 方法：用dummy node （参考随课教程）
    - 一般BST的考点都是iteration版本的traveral
- recursion是利用操作系统模拟出的栈空间
    - python强制递归层数不能超过1万层，默认900层左右
    


- iteration 版本 在随堂练习里的太复杂了看不懂，九章答案用的dummy node更直接, 同学给的答案更简单


- 递归的方法：有一个变量++，一直加到k为止；或者k--，一直减到0为止
- iteration的方法：iteration做k次

```py
#
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def kthSmallest(self, root: TreeNode, k: int) -> int:
        if not root:
            return None
        
        stack = []
        
        while root:
            stack.append(root)
            root = root.left
            
        while stack and k > 0:
            node = stack.pop()
            k -= 1

            if node.right and  k > 0:
                node = node.right
                while node:
                    stack.append(node)
                    node = node.left
        return node.val
            
            
        
```



