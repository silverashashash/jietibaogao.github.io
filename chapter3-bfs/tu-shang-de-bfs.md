## 图上的BFS
BFS in Graph

点和点之间不是父子关系而是邻居关系，因此要防止A->B->A这种情况(图中存在环)。
BFS in Graph要标记已访问过的点，通过哈希表这样的数据结构（python: dict）
