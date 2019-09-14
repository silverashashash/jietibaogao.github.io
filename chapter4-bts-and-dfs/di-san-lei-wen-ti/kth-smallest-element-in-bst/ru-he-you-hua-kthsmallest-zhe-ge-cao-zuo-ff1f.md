##如何优化kth smallest
####优化方法

在 ``TreeNode`` 中增加一个 ``counter``，代表整个树的节点个数
也可以用一个 ``HashMap<TreeNode, Integer>`` 来存储某个节点为代表的子树的节点个数 在增删查改的过程中记录不断更新受影响节点的 ``counter``(用hashmap不用修改``Treenode``的结构)
在 ``kthSmallest`` 的实现中用类似 Quick Select 的算法去找到 ``kth smallest element`` 时间复杂度为 $$O(h)$$，$$h$$ 为树的高度。
- Strong Hire: 能够答出 Follow Up 的算法，并写出kthSmallest核心代码(不需要写增删查改，45分钟写 不完的)， bug free or minor bug，不需要提示
- Hire / Weak Hire : 能够答出 Follow up 的算法，大致写出 kthSmallest 核心代码，存在一定bug，或者需 要提示
- No Hire: 答不出 follow up
- Strong No: 连第一问的 Inorder traversal 都不会写