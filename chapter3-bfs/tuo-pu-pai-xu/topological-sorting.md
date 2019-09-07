## Topological  Sorting

[http://www.lintcode.com/problem/topological-sorting/](http://www.lintcode.com/problem/topological-sorting/)

### Description

Given an directed graph, a topological order of the graph nodes is defined as follow:

* For each directed edge`A -> B `in graph, A must before B in the order list.
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

