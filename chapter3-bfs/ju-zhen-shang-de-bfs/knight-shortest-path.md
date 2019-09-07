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
* leetcode 求的是起始位置。要注意边界条件里 ``start`` 和 ``end`` 不能为1，否则会报错。

```py
# 超时的答案
"""
Definition for a point.
class Point:
    def __init__(self, a=0, b=0):
        self.x = a
        self.y = b
"""

class Solution:
    """
    @param grid: a chessboard included 0 (false) and 1 (true)
    @param source: a point
    @param destination: a point
    @return: the shortest path 
    """
    def shortestPath(self, grid, source, destination):
        # write your code here
        if not grid or not grid[0]:
            return -1

        length = {(source.x, source.y) : 0} 
        q = collections.deque([(source.x, source.y)])

        while q:
            x, y = q.popleft()
            for delta_x, delta_y in [(1, 2), (1, -2), (-1, 2), (-1, -2), (2, 1), (2, -1), (-2, 1), (-2, -1)]:              
                next_x, next_y = x + delta_x, y + delta_y
                if not self.is_valid(grid, next_x, next_x) or (next_x, next_y) in length:
                    continue
                if (next_x, next_y) == (destination.x, destination.y):
                    return length[(x,y)] + 1 
                q.append((next_x, next_y))
                length[(next_x, next_y)] = length[(x,y)] + 1 


        return -1

    def is_valid(self, grid, x, y):
        n, m = len(grid), len(grid[0])
        return 0 <= x < n and 0 <= y < m and grid[x][y] != 1
        
        #错误原因是for 循环里 调用is_valid的时候参数写错了。。。摊手
```



