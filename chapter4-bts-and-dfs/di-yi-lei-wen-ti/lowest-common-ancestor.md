## Lowest Common Ancestor of a Binary Tree
最近公共祖先
https://www.lintcode.com/problem/lowest-common-ancestor-of-a-binary-tree/
https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/

####课上的思路
分治法：
    - 左右分别找LCA
        - 左边找到：return 左边的LCA
        - 右边找到：return 右边的LCA
        - 左右都找不到：
            - 左右一边一个
            - 某个数不存在
            