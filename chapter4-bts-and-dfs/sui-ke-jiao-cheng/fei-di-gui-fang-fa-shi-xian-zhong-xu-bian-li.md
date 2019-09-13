## 非递归方法实现中序遍历 in-order

 http://www.lintcode.com/problem/binary-tree-inorder-traversal/
 
 - 参考了九章同学的答案
  - 添加所有最左边节点到栈。
  - pop stack 然后添加到结果。
  - 查找当前node的右边节点是否为空， 如果不为空，重复step 1。