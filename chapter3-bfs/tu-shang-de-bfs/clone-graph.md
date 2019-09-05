## Clone Graph

[http://www.lintcode.com/problem/clone-graph/](http://www.lintcode.com/problem/clone-graph/)  
[https://leetcode.com/problems/clone-graph/](https://leetcode.com/problems/clone-graph/)  
图的遍历（由点及面）  
deep copy：复制到不同的内存位置（修改新的不影响旧的）

* 本题没有二叉树按层遍历的需求
* $$O(m+n)$$
* 需要复制新老节点之间的映射关系（mapping）和节点之间的连接（边）
* 要用hashset存储已经经历过的点，防止图中存在环

第一步：找到所有的点  
第二步：复制所有的点，将映射关系存起来  
第三步：找到所有的边，复制每一条边

* 所谓的复制边，就是把neighbor\[\]里的所有node复制到新的node里
* 感觉看都看不明白
* 为什么是`queue = collections.deque([node])` 而二叉树是`queue.append(root)`

```py
#自己的答案
```

```py
#leetcode上的高赞回答
# BFS
def cloneGraph1(self, node):
    if not node:
        return 
    nodeCopy = UndirectedGraphNode(node.label)
    dic = {node: nodeCopy}
    queue = collections.deque([node])
    while queue:
        node = queue.popleft()
        for neighbor in node.neighbors:
            if neighbor not in dic: # neighbor is not visited
                neighborCopy = UndirectedGraphNode(neighbor.label)
                dic[neighbor] = neighborCopy
                dic[node].neighbors.append(neighborCopy)
                queue.append(neighbor)
            else:
                dic[node].neighbors.append(dic[neighbor])
    return nodeCopy
```

```py
#白书上的回答
class GraphVertex:
    def __init__(self, label)
        self.label = label
        self.edges = []

def clone_graph(G):
    if not G:
        return None

    q = collections.deque([G])
    vertex_map = {G: GraphVertex(G.label)}
    while q:
        v = q.popleft()
        for e in v.edges:
           # Try tp copy the vertex e
           if e not in vertex_map:
               vertex_map[e] = GraphVertex(e.label)
               q.append(e)
           # Copy edge v -> e
           vertex_map[v].edges.append(vertex_map[e])
   return vertex_map[G]
```

```py
#九章的答案1
"""
#Definition for a undirected graph node
class UndirectedGraphNode:
    def __init__(self, x):
        self.label = x
        self.neighbors = []
"""

class Solution:
    def cloneGraph(self, node):
        root = node
        if node is None:
            return node
        
        #Use BFS to traverse the graph and get all nodes
        node = self.getNodes(node)
        
        # Copy nodes, store the old -> new mapping information in a hash map
        mapping = {}
        for node in nodes:
            mapping[node] = UndirectedGraphNode(node.label)
        
        # Copy neighbors(edegs)
        for node in nodes:
            new_node = mapping[node]
            for neighbor in node.neighbors:
                new_neigbor = mapping[neighbor]
                new_node.neighbor.append(new_neighbor)
        
        return mapping[root]
        
    def getNode(self, node):
        q = collections.deque([node])
        result = set([node])
        while q:
            head = q.popleft()
            for neighbor in head.neighbors:
                if neighbor not in result:
                    result.add(neighbor)
                    q.append(neighbor)
        return result
        
        
        
        
        
        
        
        
        
        
        

```



