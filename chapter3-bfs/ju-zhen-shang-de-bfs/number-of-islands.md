## Number of islands

图的遍历（由点及面），通过一个点找到其他所有点，又叫连通块问题（Connected componont）。

#### Description

Given a 2d grid map of`'1'`s \(land\) and`'0'`s \(water\), count the number of islands. An island is surrounded by water and is formed by connecting adjacent lands horizontally or vertically. You may assume all four edges of the grid are all surrounded by water.

**Example 1:**

```
Input:

11110
11010
11000
00000


Output:
 1
```

**Example 2:**

```
Input:

11000
11000
00100
00011


Output: 
3
```





```py
##看了答案才写出来，但是感觉也不太难？
class Solution:
    def numIslands(self, grid: List[List[str]]) -> int:
        if not grid or not grid[0]:
            return 0 
        
        islands = 0
        visited = set()
        
        for i in range(len(grid)):
            for j in range(len(grid[0])):
                if grid[i][j] == "1" and (i, j) not in visited:
                    self.find_island(grid, i, j, visited)
                    islands += 1
        
        return islands
    
    def find_island(self, grid, x, y, visited):
        q = collections.deque([(x, y)])
        visited.add((x, y))
        
        while q:
            x, y = q.popleft()
            for (delta_x, delta_y) in [(0, 1), (1, 0), (-1, 0), (0, -1)]:
                next_x, next_y = x + delta_x, y + delta_y 
                if not self.is_island(grid, next_x, next_y, visited):
                    continue 
                q.append((next_x, next_y))
                visited.add((next_x, next_y))
    
    def is_island(self, grid, x, y, visited):
        n, m = len(grid), len(grid[0])
        return 0 <= x < n and 0 <= y < m and grid[x][y] == "1" and (x, y) not in visited
        
```



