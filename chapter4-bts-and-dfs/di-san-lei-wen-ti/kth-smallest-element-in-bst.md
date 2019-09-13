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


```py
#

```



