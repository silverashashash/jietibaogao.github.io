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
            
    - 构造return value：
        - 存在LCA: return LCA
        - 不存在LCA: 
            - 有A：return A
            - 有B：return B
            - 都没：return None
    - 代码缺点：
        - ``if root is A or root is B: return None``这里不知道return的是LCA还是A、B其中的一个点
        - 要判断LCA是不是都在这个子树里，见LCA-III这题
        



```py


```

