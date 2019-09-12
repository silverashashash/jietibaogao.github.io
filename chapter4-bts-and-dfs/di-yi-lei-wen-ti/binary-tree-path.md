## Binary Tree Path

[https://www.lintcode.com/problem/binary-tree-paths](https://www.lintcode.com/problem/binary-tree-paths)



- traveral
    - ``pop()``做回溯
    - number of islands 这题用dfs没有回溯，因为找的是所有的点（有去有回找的是路程，有去无回找的是点）
    - ``results[]``作为参数传递，好于用全局变量
    
- divide and conquer 
    - 整棵树的路径和左右子树的路径的关系？
    - 注意root是叶子结点的时候需要特殊处理（``root.right`` 和root.left都是None）
    
    
    