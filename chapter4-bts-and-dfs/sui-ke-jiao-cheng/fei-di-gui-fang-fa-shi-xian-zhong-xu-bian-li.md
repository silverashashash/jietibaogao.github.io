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
 
 ```py
 # 答案里一个简单明了的解答：
 # 添加所有最左边节点到栈。
 # pop stack 然后添加到结果。
 # 查找当前node的右边节点是否为空， 如果不为空，重复step 1。
 class Solution:
    """
    @param root: A Tree
    @return: Inorder in ArrayList which contains node values.
    """
    def inorderTraversal(self, root):
        # write your code here
        if not root:
            return []
        
        result = []
        stack = []
        
        while root:
            stack.append(root)
            root = root.left
        
        while stack:
            curNode = stack.pop()
            result.append(curNode.val)
            
            if curNode.right:
                curNode = curNode.right
                while curNode:
                    stack.append(curNode)
                    curNode = curNode.left
        
        return result
 ```
 
 ```py
 #更精简的版本
 # Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def inorderTraversal(self, root: TreeNode) -> List[int]:
        if not root:
            return []
        
        stack = []
        result = []
        node = root
        while stack or node:
            while node:
                stack.append(node)
                node = node.left
            
            node = stack.pop()
            result.append(node.val)
            
            node = node.right
        
        return result
        
 ```