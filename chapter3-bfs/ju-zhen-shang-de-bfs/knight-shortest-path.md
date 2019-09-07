## Knight Shortest Path

简单图最短路径

[https://www.lintcode.com/problem/knight-shortest-path/description](https://www.lintcode.com/problem/knight-shortest-path/description)

[https://leetcode.com/problems/shortest-path-in-binary-matrix/](https://leetcode.com/problems/shortest-path-in-binary-matrix/)  
follow up：如何加速？bidirection BFS

### Description

Given a knight in a chessboard \(a binary matrix with`0`as empty and`1`as barrier\) with a`source`position, find the shortest path to a`destination`position, return the length of the route.  
Return`-1`if destination cannot be reached.

### Clarification

If the knight is at \(_x_,_y_\), he can get to the following positions in one step:

```
(x + 1, y + 2)
(x + 1, y - 2)
(x - 1, y + 2)
(x - 1, y - 2)
(x + 2, y + 1)
(x + 2, y - 1)
(x - 2, y + 1)
(x - 2, y - 1)
```

### Example

**Example 1:**

```
Input:
[[0,0,0],
 [0,0,0],
 [0,0,0]]
source = [2, 0] destination = [2, 2] 
Output: 2
Explanation:
[2,0]->[0,1]->[2,2]
```

**Example 2:**

```
Input:
[[0,1,0],
 [0,0,1],
 [0,0,0]]
source = [2, 0] destination = [2, 2] 
Output:-1
```

* 感觉跟上面那题差不多
* pop出一个数组咋传给左边
  * 直接`x, y = q.popleft()`
* list是不能作为dict的key的，只有immutable的才可以。所以这题要把list转成tuple
* 这题的source和destination都是定义出来的Point Class，使用的时候要注意用法
* 一开始没使用visited，因为我觉得可以走回头路，结果数据大的时候超时了





