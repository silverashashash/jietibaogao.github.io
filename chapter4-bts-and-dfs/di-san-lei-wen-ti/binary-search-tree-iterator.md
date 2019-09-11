## Binary Search Tree Iterator
阅读全文并背诵

####Binary Search Tree Interator
该iterator算法即non-recursion 的 in-order traversal, 不仅仅适用于BST，任何Binary Tree 都可以
- stack 中保存一路走到当前节点的所有节点
- stack 中的栈顶 一直存储iterator指向的当前节点
- hasNext() 只需要判断stack是否为空
- next() 只需要返回 stack 的栈顶值，并将 iterator 挪到下一个点，最stack进行相应的变化

挪到下一个点的算法如下：
- 如果当前点存在右子树，那么就是右子树中“**一路向左**”最左边的那个点
- 如果当前不存在右子树，则是走到当前点的路径中，第一个左拐的点
