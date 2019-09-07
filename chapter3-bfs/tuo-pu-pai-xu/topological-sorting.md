## Topological  Sorting

[http://www.lintcode.com/problem/topological-sorting/](http://www.lintcode.com/problem/topological-sorting/)

### Description

Given an directed graph, a topological order of the graph nodes is defined as follow:

* For each directed edge`A -> B`in graph, A must before B in the order list.
* The first node in the order can be any node in the graph with no nodes direct to it.

Find any topological order for the given graph.

### Example

For graph as follow:

![](https://media-cdn.jiuzhang.com/markdown/images/8/6/91cf07d2-b7ea-11e9-bb77-0242ac110002.jpg "图片")

The topological order can be:

```
[0, 1, 2, 3, 4, 5]
[0, 2, 3, 1, 5, 4]
...
```

### Challenge

Can you do it in both BFS and DFS?

```py
#看了答案的做法
"""
Definition for a Directed graph node
class DirectedGraphNode:
    def __init__(self, x):
        self.label = x
        self.neighbors = []
"""


class Solution:
    """
    @param: graph: A list of Directed graph node
    @return: Any topological order for the given graph.
    """
    def topSort(self, graph):
        # write your code here
        if not graph:
            return []
            
        order = []
        graph_indegree = self.get_indegree(graph)
        start_node = [n for n in graph if graph_indegree[n] == 0]
        q = collections.deque(start_node)

        
        while q:
            node = q.popleft()
            order.append(node)
            for neighbor in node.neighbors:
                graph_indegree[neighbor] -= 1 
                if graph_indegree[neighbor] == 0:
                    q.append(neighbor)
                    
        return order

        
        
        
    def get_indegree(self, graph):
        
        indegree = {x : 0 for x in graph}
        
        for node in graph:
            for neighbor in node.neighbors:
                indegree[neighbor] += 1 
                
        return indegree
```
* 注意一些用法：``start_node = [n for n in graph if graph_indegree[n] == 0]``
              ``indegree = {x : 0 for x in graph}``




