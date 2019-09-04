## BFS and Topological Sorting



####先修内容

- 什么是队列， 如何自己实现一个队列
- 什么是拓扑排序 Topological Sorting
- 如何定义一个图的数据结构


####大纲

- 什么时候使用BFS
    - 图的遍历
        - 层级遍历 Level Order Traversal
        - 由点及面 Connected Coponent
        - 拓扑排序 Topology Sorting
    - 最短路径 Shortest Path in Simple Graph
        - 仅限简单图求最短路径，即图中每条边长度都是1，或者边长都相等
    - 非递归方式找所有答案 Iteration solution for all possible results
        - DFS的替代品，解决NP问题
- 二叉树上的BFS
- 图上的BFS
- 矩阵上的BFS
- 拓扑排序 Topological Sorting

 
 #### 课后补充内容
 - BFS的另外两种实现方式
 - 双向宽度优先搜索 Bidirectional BFS
 
####总结
 - 能用BFS的一定不要用DFS（除非面试官要求）
 - BFS使用的两个条件：
     - 图的遍历（由点及面，层级遍历）
     - 简单图最短路径
 - 是否需要层级遍历
     - java/c++写成``size = queue.size()``
     - python 直接写成``for i in range(len(queue))``
 - 拓扑排序必须掌握
 - 坐标变换数组
     - deltaX, deltaY
     - inBound
     
 
 


