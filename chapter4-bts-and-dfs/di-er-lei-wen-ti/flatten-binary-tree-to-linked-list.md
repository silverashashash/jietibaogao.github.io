## Flatten Binary Tree to Linked List

[https://www.lintcode.com/problem/flatten-binary-tree-to-linked-list](https://www.lintcode.com/problem/flatten-binary-tree-to-linked-list)

[https://leetcode.com/problems/flatten-binary-tree-to-linked-list/](https://leetcode.com/problems/flatten-binary-tree-to-linked-list/)

### Description

Flatten a binary tree to a fake "linked list" in pre-order traversal.

Here we use the _right_ pointer in TreeNode as the _next_ pointer in ListNode.

```
Don't forget to mark the left child of each node to null. 
Or you will get Time Limit Exceeded or Memory Limit Exceeded.

```

- 要求是in-place的，不能用pre-order先做一遍
- ``last_node``表示pre-order访问到最后一个结点是谁。如果``last_node``非空，就让上一个结点的right指向node
- 用traversal要注意``right_node``要先保存起来，否则会出bug（找不到``right_node``了）
- 用divide&conquer不容易出bug，返回一个node表示``last_node``
- 为什么要用helper函数？
- 如果不用helper函数，root is None的情况如何表示返回？



```py
#看了答案才知道的

```

