## 非递归方法实现中序遍历 in-order

 http://www.lintcode.com/problem/binary-tree-inorder-traversal/
 
 - 参考了九章同学的答案
  - 添加所有最左边节点到栈。
  - pop stack 然后添加到结果。
  - 查找当前node的右边节点是否为空， 如果不为空，重复step 1。
  
  
  
  
 ```py
 #九章的dummy node方法
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
    @return: Inorder in ArrayList which contains node values.
    """
    def inorderTraversal(self, root):
        if root is None:
            return []
            
        # 创建一个 dummy node，右指针指向 root
        # 并放到 stack 里，此时 stack 的栈顶 dummy
        # 是 iterator 的当前位置
        dummy = TreeNode(0)
        dummy.right = root
        stack = [dummy]
            
        inorder = []
        # 每次将 iterator 挪到下一个点
        # 也就是调整 stack 使得栈顶到下一个点
        while stack:
            node = stack.pop()
            if node.right:
                node = node.right
                while node:
                    stack.append(node)
                    node = node.left
            if stack:
                inorder.append(stack[-1].val)
                
        return inorder
 
 ```