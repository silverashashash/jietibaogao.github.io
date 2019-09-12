## Lowest Common Ancestor of a Binary Tree

最近公共祖先  
[https://www.lintcode.com/problem/lowest-common-ancestor-of-a-binary-tree/](https://www.lintcode.com/problem/lowest-common-ancestor-of-a-binary-tree/)  
[https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/)

#### 课上的思路

分治法：

* 左右分别找LCA
  * 左边找到：return 左边的LCA
  * 右边找到：return 右边的LCA
  * 左右都找不到：
    * 左右一边一个
    * 某个数不存在

* 构造return value：
  * 存在LCA: return LCA
  * 不存在LCA: 
    * 有A：return A
    * 有B：return B
    * 都没：return None
* 代码缺点：
  * `if root is A or root is B: return root`这里不知道return的是LCA还是A、B其中的一个点
  * 要判断LCA是不是都在这个子树里，见LCA-III这题

#### 问题：

* 比较的是node还是node.val?
  * 应该是node
* 这题前提条件是assume A, B exist in the tree，所以不要想太复杂了

```py
#看了答案之后
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def lowestCommonAncestor(self, root: 'TreeNode', p: 'TreeNode', q: 'TreeNode') -> 'TreeNode':

        if root is None:
            return None
        if root == p or root == q:
            return root

        left_LCA = self.lowestCommonAncestor(root.left, p, q)
        right_LCA = self.lowestCommonAncestor(root.right, p, q)

        if left_LCA and right_LCA:
            return root
        if left_LCA:
            return left_LCA
        if right_LCA:
            return right_LCA

        return None
```



